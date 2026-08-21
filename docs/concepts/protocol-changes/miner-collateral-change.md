---
title: Miner collateral (PRs #2953 + #2960)
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---

Miner collateral is a refundable-by-work registration bond for Bittensor subnets. Part of your registration fee stops being recycled and instead becomes locked stake you can only recover by earning emission — or by the subnet dissolving. It shipped via the collateral release train ([#2953](https://github.com/RaoFoundation/subtensor/pull/2953) → [#2960](https://github.com/RaoFoundation/subtensor/pull/2960)) and is **live on Finney mainnet at spec 437**.

> 📘 **The one-line version**
>
> It's a security deposit. A subnet can force part of your registration cost to be staked and frozen as collateral. You get it back slowly as you do validated work — and if you walk away without mining, it sits frozen on your hotkey, earning nothing.

## Is it on? Off by default

Miner collateral is **opt-in per subnet, and off everywhere until a subnet switches it on**. The controlling hyperparameter `CollateralLockShare` (**p**) defaults to `0`, and at `p = 0` there is no collateral at all — the entire registration price is recycled exactly as it was pre-feature. A subnet activates it by setting `p > 0` via `sudo_set_collateral_lock_share`, callable only by the subnet owner or root.

- **Optional for the subnet** — the owner chooses whether to enable it, and at what strength (`p` up to 95%).
- **Mandatory for the miner** — once your subnet runs `p > 0`, every registration on it is split and bonded automatically. There is no per-miner opt-out at registration; if you register, you post the bond.
- **Not retroactive** — turning `p` on (or changing it) affects future registrations only; standing collateral is never re-priced.

Everything below describes a subnet that has enabled it. On a subnet with `p = 0`, none of it applies — you just pay the normal burn.

## Why it exists

Registration on a busy subnet already costs real TAO — but today 100% of that cost is recycled (swapped to alpha, and that alpha removed from supply; the chain labels this the "burn"). Once you're registered, the value is gone to you whether you mine honestly or squat the slot doing nothing.

Miner collateral changes the incentive: a subnet owner can redirect part of the registration cost away from the burn and into a locked bond on your own hotkey. Now you have skin in the game. Mine well and the bond flows back to you. Spam-register or go idle and your capital is stuck. It's an anti-spam / commitment mechanism, tuned per subnet.

> 🚧 **Misconception to kill first**
>
> "Registration is cheap (0.001 TAO), so collateral is trivial." Not on collateral subnets. The 0.001 figure is the floor on idle subnets. A subnet that wants collateral deliberately runs a higher registration price and then splits it — that's the whole point. The feature targets those subnets, not the cheap ones.

## The split: burn vs lock

Each subnet sets a hyperparameter **p** (`CollateralLockShare`), a fraction from `0` to `0.95`. Your registration cost splits by that ratio:

```
registration cost
  └─ ALL of it → swap TAO → alpha (into the subnet's pool)
             ├─ p       → stake to your hotkey → LOCK
             └─ (1 − p) → alpha removed from supply (the "burn")
```

> 📘 The `(1 − p)` share is often called the "burn," but it's a recycle, and the chain uses that word literally. Your whole payment is swapped TAO → alpha. Two things then happen to the `(1 − p)` share: its TAO stays in the subnet and is tallied in `RAORecycledForRegistration` (the chain's recycled-TAO counter), and the alpha it bought is decremented from `SubnetAlphaOut` — removed from circulating alpha supply. It is not a TAO burn; nothing is destroyed at the TAO level.

So it's your registration money that gets locked — not extra money on top. Two things to internalise:

- **It's locked as alpha, not TAO.** Your `p` share buys the subnet's alpha token at its moving-average price (with a 5% slippage cap on the buy), and it's the alpha that's locked. Its TAO value floats afterward.
- **The "burn" share is always positive.** `p` is capped at 95% (`MaxCollateralLockShare`) so a registration always recycles something — you can never lock 100%.

### Worked example

Subnet sets reg cost = 2 TAO at the maximum `p = 0.95`, alpha price = 0.1:

| Component | Amount | Fate |
|---|---|---|
| "Burned" `(1 − p)` | 0.1 TAO | recycled (alpha removed from supply) |
| Locked `p` | 1.9 TAO → 19 alpha | frozen on your hotkey |

Change the dials and you change the bond: `p = 0.5` on the same 2 TAO reg → burn 1 / lock 1. Note the cap makes a big bond need a big reg cost: to lock ~1 TAO you need reg ≥ ~1.05 TAO, since at most 95% of it can be locked.

## How the lock comes back: drain, not decay

The lock does **not** decay on a clock. Sit idle for a year and it's exactly where you left it. The only thing that reduces it is earned emission, settled each tempo:

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/41916da217e4cdac.png" />

- **k** = `CollateralDrainRatio` — the per-subnet unlock rate. Default `1.0` (one alpha released per alpha of emission earned), settable up to `10.0`.
- Each tempo you earn emission, `k × emission` of alpha unlocks back to your free stake, where you can unstake or transfer it normally.
- `k` is snapshotted onto your position at registration. If the owner changes `k` mid-life, your existing bond keeps its original rate — only your next re-registration re-prices it.

> 📘 **Is emission locked? No — it's the opposite**
>
> A common misread: "does the feature lock my incentive?" No. Your emission pays out normally — and it's the key that unlocks your collateral. Earning emission drains your bond down. The only exception is the floor mechanic below.

Since **runtime 437** the drain settles against **full hotkey emission** — miner incentive *and* validator dividends — releasing the lock at rate `k`. (Runtime 435 drained on incentive only, which stranded pure-validator locks; 437 fixed that.)

### The optional floor (`min_locked`)

A miner can set a floor (`do_set_min_collateral`) — e.g. to track a per-machine deposit a subnet's validators publish. The lock self-maintains around it:

- **Above the floor:** emission drains the lock down toward the floor (and stops there).
- **Below the floor (you're deficient):** emission is captured — withheld from you and pushed back into the lock — until the floor is restored. This is the only path where emission doesn't reach your wallet.

The chain also tracks `earned` — cumulative lifetime emission per collateral entry — so validators can compare a miner's extraction against the bond still at risk.

## A separate lock from conviction — they stack

> 🚧 **Miner collateral is NOT a conviction lock**
>
> These are two completely independent locks with different storage, purpose, and exit rules. A single stake position can carry both at once, and they stack: when you try to unstake, the chain subtracts both the miner collateral and the conviction lock, and only what's left over is movable.

The two behave in opposite ways on the point that matters most — getting your locked stake out. Miner collateral has no transfer exit at all, where [conviction](/docs/conviction-v2) does:

| | Conviction lock | Miner collateral |
|---|---|---|
| Purpose | Voluntary — boost stake weight | Forced — registration bond |
| Storage | `Locks` | `MinerCollateral` |
| Unstake locked amount | blocked up to lock | blocked up to lock |
| Transfer stake | follows the stake (recipient must accept) | blocked — stays on origin |
| Hotkey swap | permitted | bond follows the UID via `keep_stake=false`; abandoning the lock (`keep_stake=true`) is refused with `KeepStakeBlockedByCollateral` |
| Only exit | time unlock + transfer | earned emission (or subnet dissolution) — a key swap moves the bond, it does not release it |

On the hotkey-swap row, **runtime 437 changed the collateral behaviour** (the old flat-revert `HotKeyHasCollateral` error is gone). A hotkey swap now takes a `keep_stake` flag: with `keep_stake=false` the UID and its bonded stake move together to the new hotkey — the collateral follows the UID, and a per-subnet lineage record (`HotkeySuccessor` / `HotkeyRoot`) ties old and new keys to one identity so the bond stays attributable. Only `keep_stake=true` — which would strand the lock on the dead old hotkey while the UID walks off — is refused, with `KeepStakeBlockedByCollateral`. So the bond can't be abandoned by renaming keys, but it is no longer immovable: it travels with a full swap.

> 📘 **Can I stake the frozen alpha to a validator for yield?**
>
> No. It's welded to the `(netuid, hotkey, coldkey)` position that registered — you can't move it to a validator hotkey. And on your own miner hotkey it earns no passive APY: miner hotkeys only earn incentive for scored work, not dividends. While it's frozen and you're not actively mining, it earns nothing. It is inert, illiquid capital until you mine it free.

## Deregistration & re-registration

Getting pruned (neuron deregistration) does not sell or clear your alpha — it only frees your UID slot. Your staked alpha and its lock stay in place. On re-registration, the standing lock is valued at the moving-average price and credited against the new requirement, so you pay only the shortfall.

### Three re-registration cases (same 19 locked alpha, 1.9 TAO requirement)

| Scenario | Requirement (1.9 TAO) | You pay |
|---|---|---|
| Price still 0.1 | 19 alpha = 1.9 TAO → covered | just the ~0.1 burn |
| Price rises to 0.2 | 19 alpha = 3.8 TAO → over-covered | just the ~0.1 burn (excess drains out as you mine) |
| Price drops to 0.05 | 19 alpha = 0.95 TAO → short 0.95 | buy ~19 more alpha (0.95 TAO) + 0.1 burn |

> 🚧 **Fill-or-kill top-up trap**
>
> The top-up buy is bounded at spot × 1.05 (5% slippage cap). If your top-up would push the pool more than 5% above spot, the whole re-registration reverts — no partial fill. On a thin subnet with a big top-up, add collateral in smaller chunks first (`do_add_collateral`) before re-registering.

## Is it ever truly lost?

"Burned forever" is wrong — the collateral is never destroyed (only the small `(1 − p)` burn share is). But "stuck indefinitely" is right in the walk-away case.

| What happens | Your collateral |
|---|---|
| You mine, then stop | drained back to free stake as you earned — mostly recovered |
| You re-register that hotkey later | credited against the requirement — reusable |
| Subnet is dissolved | all alpha (locked + free) pro-rata converted to free TAO and returned to your coldkey; the lock rows are wiped |
| You quit, never mine, never re-reg, subnet lives on | frozen indefinitely — still yours, but non-earning & illiquid |
| Value recycled (not returned) | only the `(1 − p)` registration share — swapped to alpha, alpha removed from supply (the "burn") |

> 📘 **Subnet dissolution refunds you**
>
> On dissolution the chain runs a settlement that values every staker's alpha — collateral included — and pays it out as free TAO to the coldkey, then clears the `MinerCollateral` rows as dead metadata. So on subnet death, you get your money back.

The realistic verdict: for a live subnet you walk away from, the collateral is "lost for the foreseeable future" — not burned, not lost to the chain, still your alpha, but frozen, non-earning, and unmovable until you mine it down or re-register. The real cost is opportunity cost, plus alpha-price drift: you get your alpha back, not your TAO. If alpha craters while locked, so does the value you recover.

## What this changes for Taostats: available ≠ total

Miner collateral makes a position's displayed stake diverge from its spendable stake. Anyone reading a stake balance on a collateral subnet will overstate liquidity unless collateral is subtracted.

| Concept | Source | Meaning |
|---|---|---|
| Total stake | existing stake storage | what shows on the position today |
| Locked collateral | `MinerCollateral (netuid, hotkey, coldkey)` | frozen — can't unstake or transfer; a hotkey swap moves it with the UID but never releases it |
| Available | `stake − collateral − conviction lock` | what's actually movable |

The chain computes this internally (`available_to_unstake_from_hotkey` does `stake − collateral`, stacking with conviction locks). Surfaces to index (live as of runtime 437): `MinerCollateral`, `ColdkeyMinerCollateral`, `CollateralLockShare` (p), `CollateralDrainRatio` (k); events `CollateralLocked`, `CollateralLockShareSet`, `MinCollateralSet`; plus lineage (`ColdkeyCollateralHotkeys`, `HotkeySuccessor` / `HotkeyRoot`, `ColdkeySuccessor` / `ColdkeyRoot`).

## Who controls the dials

| Knob | Set by | Bounds | Notes |
|---|---|---|---|
| **p** — lock share | root or subnet owner | 0 – 0.95 | future registrations only; standing collateral never re-priced |
| **k** — drain ratio | root or subnet owner | >0 – 10.0 (default 1.0) | snapshotted per position at registration |
| `min_locked` — floor | the miner (own hotkey) | ≥ 0 (0 = off) | drain stops at floor; emission refills below it |
| top-up | the miner | — | `do_add_collateral`; prefers free staked alpha, buys the shortfall; keeps drain snapshot |

## The whole thing in 8 lines

1. A subnet sets **p**: your registration cost splits into a recycled share `(1 − p)` and a locked share `p`.
2. The locked share buys alpha, stakes it to your hotkey, and freezes it as collateral.
3. You recover it by earning emission: since runtime 437 the drain settles against **full hotkey emission** — miner incentive and validator dividends — releasing the lock back to free stake at rate `k`.
4. It doesn't decay on a clock — no work, no unlock.
5. You can't transfer or unstake it; a hotkey swap carries the bond to the new key (via `keep_stake=false` + lineage) but can't abandon it — and it earns no passive APY.
6. Dereg keeps it; re-registration credits it against the new requirement.
7. Subnet dissolution refunds it as free TAO. It's never destroyed — only the `(1 − p)` share is recycled.
8. For Taostats: track `available = total − collateral − conviction lock`, or balances will read too high.

## Source provenance

- **Subtensor PRs:** [#2953 — The v435 upgrade: miner registration collateral](https://github.com/RaoFoundation/subtensor/pull/2953) (merged 2026-07-21), [#2960 — Runtime 437: collateral, key lineage, and bonded swap hardening](https://github.com/RaoFoundation/subtensor/pull/2960) (merged 2026-07-22).
- **Code locations (branch `main`, spec 437):** `pallets/subtensor/src/subnets/collateral.rs`, `subnets/dissolution.rs`, `coinbase/run_coinbase.rs`, `swap/hotkey_lineage.rs`, `swap/coldkey_lineage.rs`, `pallets/subtensor/src/lib.rs` (bounds & storage), `pallets/admin-utils/src/lib.rs` (setters).
- **Status:** live on Finney mainnet — spec 437.
- **Original explainer:** prepared by Rufus for the Taostats team.

> 📘 The `#2953` / `#2960` PRs are on the `RaoFoundation/subtensor` fork used for the collateral release train. Runtime numbers: the feature landed at runtime **435** and was hardened at runtime **437** (the live spec) — the emission-based drain and bonded key-swap lineage described above are read from `main` at spec 437.
