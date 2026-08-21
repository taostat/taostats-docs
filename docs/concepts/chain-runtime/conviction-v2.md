---
title: Conviction
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

## 1. What is conviction?

Conviction is Bittensor's governance mechanism that ties voting power to long-term commitment. When you lock alpha tokens to a subnet, you earn conviction — a measure of your stake's weight in governance decisions and subnet ownership.

Conviction exists to:

- Reward long-term alignment over short-term speculation
- Provide subnet governance stability
- Enable subnet ownership transitions through the **subnet king** mechanism
- Create skin-in-the-game for validators and subnet owners

Locks are perpetual by default, subnet owners receive instant conviction, and the unlock queue was eliminated in favor of exponential decay.

## 2. How locking works

To earn conviction, you lock alpha tokens using the `lock_stake` extrinsic:

- **One lock per coldkey per subnet** — You can only have a single active lock targeting one hotkey on each subnet.
- **Lock to a hotkey** — Your locked alpha is associated with a specific hotkey on that subnet. This is typically the subnet owner's hotkey, or the hotkey of someone building conviction to challenge for subnet ownership.
- **Top-ups must match** — Additional locks to the same subnet must target the same hotkey; you can't split locks across multiple hotkeys.
- **Perpetual by default** — Locked mass stays constant indefinitely, allowing conviction to grow toward 100%.
- **Optional decay** — Call `set_perpetual_lock(false)` to enable exponential decay if you want to eventually unstake.

> 📘 **Conviction locking and staking are separate — you can do both with the same alpha**
>
> Conviction locking (via `lock_stake`) and regular [staking](/docs/staking-in-dtao) are **different methods** and don't have to point at the same hotkey. You can **lock to the subnet owner's hotkey** to build conviction and show support for the owner, while **staking the same alpha to a different, higher-performing hotkey** (for example, a Taostats validator). That way you maximize your alpha staking rewards *and* keep your conviction directed at the owner.

## 3. Two types of locks

### Perpetual locks (default)

When you lock alpha without toggling decay, your lock is perpetual:

- `locked_mass` remains constant forever
- `conviction` grows exponentially from 0 toward `locked_mass`
- Conviction asymptotically approaches 99% after 1 year, 99.9%+ after 2 years
- **Cannot unstake** — perpetual locks stay locked unless you toggle to decaying mode

### Decaying locks

After calling `set_perpetual_lock(false)`, your lock begins exponential decay:

- `locked_mass` decays with `UnlockRate` (158.6 day time constant)
- `conviction` follows a coupled decay/growth formula driven by `MaturityRate` (79.3 day time constant)
- After 365 days, **90% of locked mass has decayed** (by design)
- You can unstake the difference between your original lock and current `locked_mass`

### Subnet-owner locks

Subnet owners receive special treatment:

- **Instant conviction** — conviction equals `locked_mass` immediately (no growth period)
- **Auto-locked owner cut** — The owner's share of emissions is automatically locked each block, building conviction continuously
- Owner locks are perpetual by default but can opt into decay

## 4. The numbers

### System parameters

| Parameter | Value (blocks) | Value (days) | Meaning |
|---|---:|---:|---|
| `UnlockRate` | 1,142,108 | 158.6 (τ) | Time constant for locked mass decay. 90% decays in 365 days. |
| `MaturityRate` | 571,054 | 79.3 (τ) | Time constant for conviction growth. 2× faster than unlock rate. Half-life: 55 days. |
| Half-life (decay) | ~792,000 | 110 | Time for locked mass to decay to 50% (decaying locks only). MaturityRate half-life is 55 days. |

### Conviction growth timeline (perpetual lock)

How conviction grows over time when `locked_mass` stays constant:

| Days elapsed | Conviction (% of `locked_mass`) |
|---:|---:|
| 0 | 0.0% |
| 30 | 31.5% |
| 60 | 53.1% |
| 90 | 67.8% |
| 120 | 78.0% |
| 159 (τ) | 86.5% |
| 180 | 89.7% |
| 240 | 95.1% |
| 365 | 99.0% |

### Locked-mass decay timeline (decaying lock)

How `locked_mass` decays after toggling `set_perpetual_lock(false)`:

| Days elapsed | Locked mass remaining |
|---:|---:|
| 0 | 100.0% |
| 30 | 82.8% |
| 60 | 68.5% |
| 90 | 56.7% |
| 110 (half-life) | 50.0% |
| 120 | 46.9% |
| 159 (τ) | 36.8% |
| 365 | 10.0% |

## 5. Worked example

**Scenario:** a validator locks 10,000 alpha on subnet 64 to their hotkey.

### Phase 1: perpetual lock (default)

`locked_mass = 10,000 alpha` (constant)

| Time | Conviction | Can unstake |
|---|---:|---:|
| Day 0 | 0 alpha | 0 alpha |
| Day 30 | 3,150 alpha | 0 alpha |
| Day 60 | 5,310 alpha | 0 alpha |
| Day 90 | 6,780 alpha | 0 alpha |
| Day 120 | 7,800 alpha | 0 alpha |
| Day 180 | 8,970 alpha | 0 alpha |
| Day 365 | 9,900 alpha | 0 alpha |

> 🚧 Perpetual locks cannot be unstaked. Locked mass stays at 10,000 alpha forever.

### Phase 2: toggle to decaying

At day 365, the validator calls `set_perpetual_lock(false)`. Now both `locked_mass` and `conviction` evolve:

| Days since toggle | Locked mass | Conviction | Can unstake |
|---:|---:|---:|---:|
| 0 | 10,000 | 9,900 | 0 |
| 30 | 8,280 | 8,530 | 1,720 |
| 60 | 6,850 | 7,280 | 3,150 |
| 90 | 5,670 | 6,160 | 4,330 |
| 120 | 4,690 | 5,180 | 5,310 |
| 159 (τ) | 3,680 | 4,090 | 6,320 |
| 365 | 1,000 | 1,090 | 9,000 |

Unstakeable amount = original lock (10,000) − current `locked_mass`.

After 1 year of decay, the validator can unstake 9,000 alpha, leaving 1,000 still locked.

## 6. Subnet-owner locks

Subnet owners accumulate locked alpha automatically and receive immediate conviction:

- **Owner cut auto-locked:** Each block, the owner's emissions share is locked to their subnet ownership hotkey.
- **No initial alpha distribution:** Subnet registration does not distribute initial alpha to the owner. Conviction builds solely through the auto-locked owner cut from ongoing emissions.
- **Instant conviction:** Unlike validators, owners don't wait for conviction to grow — `conviction = locked_mass` immediately.
- **Perpetual by default:** Owner locks don't decay unless the owner explicitly calls `set_perpetual_lock(false)`.
- **Aggregate tracking:** All owner locks on a subnet are aggregated into `OwnerLock` storage for subnet king calculations.

This instant conviction ensures subnet owners always have governance weight proportional to their locked stake without waiting periods.

## 7. Subnet king mechanism

After a subnet has been active for 1 year (365.25 days), ownership can transfer via the **subnet king** mechanism.

### Eligibility requirements

- Subnet must be at least 365.25 days old.
- A **single hotkey's own rolled aggregate conviction** must exceed **18% of eligible alpha**, where eligible alpha = `SubnetAlphaOut − SubnetProtocolAlpha − AlphaBurned`. The subtraction saturates at zero, so a subnet with zero eligible alpha can never transfer ownership. The bar is measured on the winning hotkey alone — the subnet-wide total no longer counts, so other keys' locks (including the incumbent owner's) do not add to a challenger's threshold.
- The hotkey with the highest aggregate conviction is the candidate, and that same hotkey must clear the 18% bar by itself. Conviction is aggregated per hotkey (from all coldkeys locking to that hotkey), not per coldkey.

> 📘 **Reading eligible alpha from the API**
>
> You don't have to compute `SubnetAlphaOut − SubnetProtocolAlpha − AlphaBurned` yourself. The Taostats [dTAO pool](/api-reference/) endpoint exposes this exact quantity as the **`alpha_staked`** field (`GET /api/dtao/pool/latest/v1?netuid=<n>`). To check how close a subnet is to a takeover, compare a hotkey's rolled conviction against `0.18 × alpha_staked`.

> 📘 **Changed in runtime spec 447**
>
> Before spec 447, ownership transferred once the **subnet-wide total** rolled conviction (all hotkeys and coldkeys combined, including the owner) reached **10% of eligible alpha**. Spec 447 replaced that with an **18% bar on a single hotkey's own conviction**. Summing across all lockers let unrelated stakers — the incumbent owner included — inadvertently supply a challenger's quorum; gating on the winner's own conviction closes that path. Coalitions still work because backers lock directly to the challenger's hotkey, so their conviction lands in that hotkey's aggregate.

### How it works

1. **Aggregate calculation:** For each hotkey, the system sums rolled conviction across all locks targeting it — `HotkeyLock + DecayingHotkeyLock + OwnerLock` (and the decaying owner lock) — via a single shared computation (`subnet_king_with_conviction`), so selection and the admission gate can never disagree.
2. **Comparison:** The hotkey with the highest aggregate conviction is the subnet king candidate. Ownership transfers only if **that hotkey's own conviction exceeds 18% of eligible alpha** — the subnet-wide sum is not used. The comparison is cross-multiplied in 256-bit integers so high-range takeovers can't saturate.
3. **Transfer:** Ownership transfers, and the lock aggregates swap:
   - Old owner's `OwnerLock` → becomes non-owner locks
   - New owner's non-owner locks → become `OwnerLock`
4. **Instant conviction retained:** The new owner keeps their conviction value but now has instant-conviction status for future locks.

**Design rationale:** This mechanism prevents permanent ownership monopolies while requiring challengers to demonstrate long-term commitment through locked alpha and conviction growth.

## 8. What you can and can't do

### ✅ Allowed actions

- **Top up existing lock:** Add more alpha to your existing lock (must target the same hotkey).
- **Move lock to a different hotkey:** You can move your lock to a different hotkey on the same subnet. If the destination hotkey is owned by the same coldkey, conviction is preserved. If owned by a different coldkey, conviction resets to zero.
- **Toggle decay mode:** Switch between perpetual and decaying at any time with `set_perpetual_lock`.
- **Partial unstaking (decaying only):** Unstake the difference between original lock and current `locked_mass`.

### ❌ Not allowed

- **Unstake perpetual locks:** You must first toggle to decaying mode and wait for mass to decay.
- **Cross-subnet transfers:** Locks are subnet-specific and cannot be moved between subnets.
- **Multi-hotkey locks:** You cannot have multiple locks to different hotkeys on the same subnet from one coldkey.
- **Lock hotkey changes:** If you have an active lock on a subnet, you can't lock to a different hotkey without first removing the existing lock.
- **Coldkey swap with active locks on destination:** A coldkey swap requires the destination coldkey to have no active locks. The source coldkey's locks transfer to the destination, but only if the destination is clean.

## 9. Technical reference

### Storage maps

| Storage | Key | Value | Purpose |
|---|---|---|---|
| `Lock` | (coldkey, netuid) | `LockState` | Legacy/compatibility — tracks basic lock state |
| `HotkeyLock(netuid, hotkey)` | (coldkey, netuid, hotkey) | `LockState` | Aggregate conviction from all perpetual (non-decaying) non-owner coldkeys locking to this hotkey on this subnet |
| `DecayingHotkeyLock(netuid, hotkey)` | (coldkey, netuid, hotkey) | `LockState` | Aggregate conviction from all decaying non-owner coldkeys locking to this hotkey on this subnet |
| `OwnerLock(netuid)` | (coldkey, netuid) | `LockState` | Aggregate conviction for the subnet owner coldkey's lock on this subnet |
| `DecayingLock(coldkey, netuid)` | (coldkey, netuid) | `LockState` | Per-coldkey flag: when present, that coldkey's lock decays. Missing = perpetual. |

### `LockState` structure

```rust
LockState {
  locked_mass: u64,   // Current locked alpha (decays if non-perpetual)
  conviction: u64,    // Governance weight (grows/decays based on mode)
  last_update: u64    // Block number of last state update
}
```

### Roll-forward formula

When reading lock state, the system rolls forward from `last_update` to the current block. With `dt = current_block − last_update` blocks elapsed, the decay factors and coupling term are:

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/f1d328cc5f83e00c.png" />

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/7470ec65bd4219e6.png" />

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/d8265ab6b51f343c.png" />

The locked mass either holds (perpetual locks) or decays:

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/0ec6d43bda99addd.png" />

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/21767c007584984b.png" />

For subnet owners with instant conviction, the formula simplifies to `conviction = locked_mass` (no roll-forward needed for conviction growth).

### Key extrinsics

- `lock_stake(hotkey, netuid, amount)` — Lock alpha to a hotkey on a subnet (perpetual by default).
- `set_perpetual_lock(netuid, perpetual: bool)` — Toggle between perpetual (`true`) and decaying (`false`) mode.
