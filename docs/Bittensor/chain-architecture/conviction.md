---
title: Conviction
excerpt: >-
  Conviction is a new (May 2026) feature allowing locking alpha to a subnet to
  show conviction (reduces rugpulls)
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

# Bittensor Conviction System v2
Technical Explainer — Based on subtensor PRs #2658 and #2687

_Last updated: 2026-05-27 (post PR #2696 60-day rates + pending PR #2695 no-default-auto-lock)._

## Mainnet vs devnet-ready right now

| | mainnet | devnet-ready / testnet |
|---|---|---|
| spec_version | 402 | 410 |
| Conviction system | v1 (old) | v2 (PR #2687) |
| UnlockRate / MaturityRate | n/a | 648,000 blocks (~60-day half-life, PR #2696) |
| Default lock mode | n/a | decaying (perpetual is opt-in) |
| Owner-cut auto-lock default | n/a | true today; **flips to false** when PR #2695 merges |

Mainnet deploy PR #2643 is open but blocked on the `breaking-change` review gate. None of the v2 behavior is live on mainnet yet.

## What changed in this update

Three PRs reshaped conviction v2 between 2026-05-25 and 2026-05-27, all landing on `devnet-ready`:

- **PR #2687 "Conviction updates"** — merged 2026-05-25. Decaying is now the default lock mode, perpetual is opt-in via `set_perpetual_lock(true)`. Anyone locking to the subnet owner's hotkey gets immediate conviction. One `ConvictionModel` struct with 4 aggregates. New RPC `get_coldkey_lock(coldkey, netuid) -> Option<LockState>`. Deprecated conviction maps removed. Testnet state wiped by `migrate_reset_tnet_conviction_locks`.
- **PR #2696 "60 day unlock and maturity rate"** — merged 2026-05-26 (commit `cee0eda`). `DefaultUnlockRate` and `DefaultMaturityRate` both changed from `311_622` (~30-day half-life) to `648_000` blocks (~60-day half-life). `spec_version` 408 → 409.
- **PR #2695 "No default auto-lock"** — *open, mergeable but blocked on review approvals*. `DefaultOwnerCutAutoLockEnabled` flips from `true` to `false`. `spec_version` 409 → 410. Subnets must opt in via `sudo_set_owner_cut_auto_lock_enabled(netuid, true)` once this ships.

The rest of this document reflects the post-#2696 / pending-#2695 picture (defaults: 60-day half-life, decaying mode, owner-cut auto-lock OFF by default).

## 1. What Is Conviction?

Conviction is Bittensor's governance mechanism that ties voting power to long-term commitment. When you lock alpha tokens to a subnet, you earn **conviction** — a measure of your stake's weight in governance decisions and subnet ownership.

Conviction exists to:

- Reward long-term alignment over short-term speculation
- Provide subnet governance stability
- Enable subnet ownership transitions through the "subnet king" mechanism
- Create skin-in-the-game for validators and subnet owners

Version 2 fundamentally redesigned the system: locks are now **decaying by default** (opt-in to perpetual via `set_perpetual_lock(true)`), anyone locking to the **subnet owner's hotkey** receives **instant conviction**, and the unlock queue was eliminated in favor of exponential decay.

## 2. How Locking Works

To earn conviction, you lock alpha tokens using the `lock_stake(hotkey, netuid, amount)` extrinsic:

- **One lock per coldkey per subnet** — You can only have a single active lock targeting one hotkey on each subnet.
- **Lock to a hotkey** — Your locked alpha is associated with a specific hotkey on that subnet. This is typically the subnet owner's hotkey, or the hotkey of someone building conviction to challenge for subnet ownership.
- **Top-ups must match** — Additional locks to the same subnet must target the same hotkey; you can't split locks across multiple hotkeys.
- **Decaying by default** — New locks decay automatically. `locked_mass` shrinks exponentially over time, and the difference between original lock and current mass can be unstaked.
- **Optional perpetual** — Call `set_perpetual_lock(netuid, true)` to freeze `locked_mass` and let conviction grow toward 100%.

## 3. Lock Types and Storage Buckets

Conviction v2 uses one **individual lock state** per locking coldkey plus **four aggregate buckets** based on two dimensions: who you lock TO (owner hotkey vs non-owner hotkey) and lock mode (perpetual vs decaying).

### The Four Aggregate Buckets

| Bucket | Lock Target | Mode | Conviction | Storage |
|---|---|---|---|---|
| **OwnerLock** | Owner hotkey | Perpetual | **Instant** | `OwnerLock(netuid)` |
| **DecayingOwnerLock** | Owner hotkey | Decaying | **Instant** | `DecayingOwnerLock(netuid)` |
| **HotkeyLock** | Non-owner hotkey | Perpetual | Normal maturity curve | `HotkeyLock(netuid, hotkey)` |
| **DecayingHotkeyLock** | Non-owner hotkey | Decaying | Normal maturity curve | `DecayingHotkeyLock(netuid, hotkey)` |

The individual lock state (per coldkey, per subnet) is rolled forward into one of these 4 aggregates depending on the lock target and mode. The `ConvictionModel` struct in `staking/lock.rs` maintains all 5 states (1 individual + 4 aggregates) and updates them atomically on every operation.

### Key rule: Locking to the subnet owner's hotkey gives instant conviction

Anyone — not just the subnet owner — who locks alpha to the **subnet owner's hotkey** receives **instant conviction**. This applies regardless of whether the lock is perpetual or decaying. The conviction equals locked_mass immediately with no growth period.

Locking to any other hotkey follows the standard maturity curve (1-month half-life under the new defaults, ~95% conviction at ~4.3 months).

### Decaying Locks (Default)

When you call `lock_stake` without first opting into perpetual mode, your lock is **decaying**:

- `locked_mass` decays exponentially with **UnlockRate** (default 648,000 blocks = ~60-day half-life)
- `conviction` follows a coupled decay/growth formula driven by **ConvictionMaturityRate** (default 648,000 blocks = ~60-day half-life) — unless locked to the owner hotkey, in which case conviction tracks locked_mass directly
- After ~60 days, half of locked mass has decayed
- You can unstake the difference between your original lock and current `locked_mass`

The fact that both timescales are equal (648,000) under the new defaults means the coupling factor between `locked_mass` decay and `conviction` decay simplifies considerably — they track each other much more closely than they did under the v2 pre-update defaults.

### Perpetual Locks (Opt-In)

After calling `set_perpetual_lock(netuid, true)`, your lock becomes **perpetual**:

- `locked_mass` remains constant
- `conviction` grows exponentially from current value toward `locked_mass` (non-owner hotkey) OR equals `locked_mass` instantly (owner hotkey)
- Cannot unstake — perpetual locks stay locked unless you toggle back to decaying mode with `set_perpetual_lock(netuid, false)`

### Subnet Owner's Own Locks

Subnet owners receive additional treatment:

- **Auto-locked owner cut** — The owner's share of emissions is automatically locked each block, building conviction continuously. Togglable per subnet by the owner via `sudo_set_owner_cut_auto_lock_enabled(netuid, enabled)`. `DefaultOwnerCutAutoLockEnabled` is currently `true` on devnet-ready, **but PR #2695 (open, blocked on review) flips it to `false`** — once that ships owners must explicitly enable auto-lock per subnet.
- Owner locks follow the same default-decaying behaviour as everyone else; opt into perpetual with `set_perpetual_lock(true)`.
- Since owners lock to their own hotkey, they get instant conviction like anyone else locking to the owner hotkey.

## 4. The Numbers

### System Parameters (Post PR #2687 Defaults)

| Parameter | Value (blocks) | Value (days) | Meaning |
|---|---|---|---|
| **UnlockRate** | 648,000 | ~60 (half-life) | Decay timescale for locked_mass on decaying locks. 50% remaining at 60 days. |
| **ConvictionMaturityRate** | 648,000 | ~60 (half-life) | Maturity timescale for conviction growth. 50% of locked_mass reached at 60 days. |

Both rates can be tuned by root via admin-utils extrinsics. Under the v2 pre-update defaults (UnlockRate 1,142,108 / MaturityRate 216,000) the system had a 5.3x speed gap between unlock and maturity — the new equal defaults remove that gap, making `locked_mass` and `conviction` decay/grow at the same fundamental pace.

### Conviction Growth Timeline (Perpetual Lock to a Non-Owner Hotkey)

How conviction grows over time when `locked_mass` stays constant, under the new 60-day half-life:

| Days Elapsed | Conviction (% of locked_mass) |
|---|---|
| 0 | 0.0% |
| 7 | ~7.8% |
| 14 | ~14.9% |
| 30 | ~29.3% |
| 60 (half-life) | 50.0% |
| 90 | ~64.6% |
| 120 | 75.0% |
| 180 | 87.5% |
| 365 | ~98.5% |

### Locked Mass Decay Timeline (Decaying Lock — the default)

How `locked_mass` decays under the new 60-day half-life:

| Days Elapsed | Locked Mass Remaining |
|---|---|
| 0 | 100.0% |
| 7 | ~92.2% |
| 14 | ~85.1% |
| 30 | ~70.7% |
| 60 (half-life) | 50.0% |
| 90 | ~35.4% |
| 120 | 25.0% |
| 180 | 12.5% |
| 365 | ~1.5% |

So in practice: a lock left in default-decaying mode is down to ~12.5% after 6 months and ~1.5% after a year. To build durable conviction you need to opt into perpetual.

## 5. Worked Example

**Scenario:** A validator locks 10,000 alpha on subnet 64 to their own (non-owner) hotkey, then opts into perpetual mode immediately.

### Phase 1: Perpetual Lock (after `set_perpetual_lock(64, true)`)

`locked_mass = 10,000 alpha` (constant while perpetual)

| Time | Conviction | Can Unstake |
|---|---|---|
| Day 0 | 0 alpha | 0 alpha |
| Day 7 | ~780 alpha | 0 alpha |
| Day 30 | ~2,930 alpha | 0 alpha |
| Day 60 | 5,000 alpha | 0 alpha |
| Day 90 | ~6,460 alpha | 0 alpha |
| Day 120 | 7,500 alpha | 0 alpha |
| Day 180 | 8,750 alpha | 0 alpha |
| Day 365 | ~9,850 alpha | 0 alpha |

**Note:** Perpetual locks cannot be unstaked. Locked mass stays at 10,000 alpha until you toggle decay back on.

### Phase 2: Toggle to Decaying

At day 365, the validator calls `set_perpetual_lock(64, false)`. Now both `locked_mass` and `conviction` decay together with the same 60-day half-life (starting from the day-365 value, ~9,850):

| Days Since Toggle | Locked Mass | Conviction | Can Unstake |
|---|---|---|---|
| 0 | ~9,850 | ~9,850 | ~150 |
| 30 | ~6,960 | ~6,960 | ~3,040 |
| 60 | 4,925 | 4,925 | 5,075 |
| 90 | ~3,480 | ~3,480 | ~6,520 |
| 180 | ~1,230 | ~1,230 | ~8,770 |
| 365 | ~145 | ~145 | ~9,855 |

After 1 year of decay, the validator can unstake essentially all of the original 10,000 alpha.

### Scenario B: Lock Directly Without Perpetual Opt-In

Same lock but the validator never calls `set_perpetual_lock`. The lock decays from day 0:

| Days Elapsed | Locked Mass | Conviction | Can Unstake |
|---|---|---|---|
| 0 | 10,000 | 0 | 0 |
| 7 | ~9,220 | ~750 | ~780 |
| 30 | ~7,070 | ~2,450 | ~2,930 |
| 60 | 5,000 | ~3,470 | 5,000 |
| 90 | ~3,540 | ~3,680 | ~6,460 |
| 180 | ~1,250 | ~1,620 | ~8,750 |

Decaying-mode conviction tracks closely behind `locked_mass` because both share the same 60-day timescale.

## 6. Subnet Owner Locks & Instant Conviction

Instant conviction applies to anyone locking to the subnet owner's hotkey, not just the owner themselves:

- **Any staker** who locks alpha to the owner's hotkey gets `conviction = locked_mass` immediately.
- **Owner cut auto-locked** (when `OwnerCutAutoLockEnabled[netuid] = true`): Each block, the owner's emissions share is automatically locked to their subnet ownership hotkey. **PR #2695 (pending) flips the default to `false`** — once merged, subnets won't auto-lock unless the owner explicitly enables it via `sudo_set_owner_cut_auto_lock_enabled(netuid, true)`. Currently default is `true` on devnet-ready.
- **No initial alpha distribution:** In v2, subnet registration does not distribute initial alpha to the owner. Conviction builds solely through the auto-locked owner cut from ongoing emissions (if enabled) or via the owner manually locking.
- **Decaying by default:** Owner locks also default to decaying mode. The owner can opt into perpetual with `set_perpetual_lock(netuid, true)`.
- **Aggregate tracking:** Owner-targeted locks are split into `OwnerLock` (perpetual) and `DecayingOwnerLock` (decaying) storage maps.

### Incentive Implications

- Independent validators become less attractive for conviction-focused stakers (they must wait through maturity).
- Subnet owners benefit from a gravitational pull of locks toward their hotkey.
- Owners can disable the owner-cut auto-lock if they want their emission share to remain unlocked/liquid, at the cost of slower personal conviction growth.
- Because decaying is now default, casual lockers will silently lose conviction over time if they never opt into perpetual — a friction point worth highlighting in the UI.

## 7. Subnet King Mechanism

**Note: The subnet king mechanism is currently disabled by design.** The code exists but the ownership-transfer call is commented out. When enabled, the rules would be:

After a subnet has been active for **1 year** (365.25 days), ownership could transfer via the "subnet king" mechanism:

### Eligibility Requirements

- Subnet must be at least 365.25 days old
- Total rolled conviction across the **entire subnet** (all hotkeys, all coldkeys, including owner) must be at least **10% of SubnetAlphaOut**. This is a subnet-wide gate, not per-challenger.
- The **hotkey** with the highest aggregate conviction wins. Conviction is aggregated per hotkey (from all coldkeys locking to that hotkey), not per coldkey.

### How It Works

- **Aggregate calculation:** The system sums conviction across all locks for each hotkey using the relevant aggregate (`HotkeyLock` + `DecayingHotkeyLock` for non-owner, `OwnerLock` + `DecayingOwnerLock` for the current owner).
- **Comparison:** The hotkey with the highest total conviction becomes the subnet king.
- **Transfer:** Ownership transfers, and the lock aggregates swap:
  - Old owner's `OwnerLock` / `DecayingOwnerLock` → become non-owner `HotkeyLock` / `DecayingHotkeyLock` against the old owner's hotkey
  - New owner's non-owner `HotkeyLock` / `DecayingHotkeyLock` → become `OwnerLock` / `DecayingOwnerLock`
- **Instant conviction retained:** The new owner keeps their conviction value but now has instant-conviction status for future locks to their hotkey.

**Design rationale:** This mechanism prevents permanent ownership monopolies while requiring challengers to demonstrate long-term commitment through locked alpha and conviction growth.

## 8. What You Can and Can't Do

### [YES] Allowed Actions

- **Top up existing lock:** Add more alpha to your existing lock (must target the same hotkey)
- **Move lock to a different hotkey:** You can move your lock to a different hotkey on the same subnet. If the destination hotkey is owned by the *same coldkey*, conviction is preserved. If owned by a *different coldkey*, conviction resets to zero.
- **Toggle decay mode:** Switch between perpetual and decaying at any time with `set_perpetual_lock(netuid, perpetual_flag)`
- **Partial unstaking (decaying only):** Unstake the difference between original lock and current `locked_mass`
- **Owner: disable own-subnet auto-lock:** Subnet owner can toggle `sudo_set_owner_cut_auto_lock_enabled(netuid, false)` to stop the owner cut from being auto-locked.

### [NO] Not Allowed

- **Unstake perpetual locks:** You must first toggle to decaying mode and wait for mass to decay.
- **Cross-subnet transfers:** Locks are subnet-specific and cannot be moved between subnets.
- **Multi-hotkey locks:** You cannot have multiple locks to different hotkeys on the same subnet from one coldkey.
- **Lock hotkey changes:** If you have an active lock on a subnet, you can't lock to a different hotkey without first removing the existing lock.
- **Coldkey swap with active locks on destination:** A coldkey swap requires the destination coldkey to have **no active locks**. The source coldkey's locks transfer to the destination, but only if the destination is clean.

## 9. Technical Reference

### Storage Maps

| Storage | Key | Value | Purpose |
|---|---|---|---|
| `Lock` | (coldkey, netuid) | LockState | Per-coldkey individual lock state (one entry per coldkey×subnet). |
| `HotkeyLock(netuid, hotkey)` | (netuid, hotkey) | LockState | Aggregate from all perpetual non-owner coldkeys locking to this hotkey. |
| `DecayingHotkeyLock(netuid, hotkey)` | (netuid, hotkey) | LockState | Aggregate from all decaying non-owner coldkeys locking to this hotkey. |
| `OwnerLock(netuid)` | (netuid) | LockState | Total perpetual lock to the owner hotkey (from ALL coldkeys, instant conviction). |
| `DecayingOwnerLock(netuid)` | (netuid) | LockState | Total decaying lock to the owner hotkey (from ALL coldkeys, instant conviction). |
| `DecayingLock(coldkey, netuid)` | (coldkey, netuid) | bool | Per-coldkey decay flag. **Missing entries mean the lock decays by default**; an explicit `false` value marks the lock as perpetual. |
| `OwnerCutAutoLockEnabled(netuid)` | (netuid) | bool | Whether owner cut auto-lock is on for this subnet. Default `true` today, **flips to `false`** with PR #2695. |
| `UnlockRate` | — | u64 | Decay timescale (blocks). Default 648,000. |
| `ConvictionMaturityRate` | — | u64 | Maturity timescale (blocks). Default 648,000. |

### LockState Structure

```rust
pub struct LockState {
    pub locked_mass: AlphaBalance,  // Current locked alpha (decays if non-perpetual)
    pub conviction: U64F64,         // Governance weight (grows/decays based on mode)
    pub last_update: u64,           // Block number of last roll-forward
}
```

### Roll-Forward Formula

When reading lock state, the system rolls forward from `last_update` to the current block:

```
// Time elapsed in blocks
dt = current_block - last_update

// Decay factors
decay_x = exp(-dt / UnlockRate)              // = exp(-dt / 648,000)
decay_z = exp(-dt / ConvictionMaturityRate)  // = exp(-dt / 648,000)

// Coupling factor — simplifies because rates are equal under new defaults
gamma = UnlockRate * (decay_x - decay_z) / (UnlockRate - MaturityRate)
// When UnlockRate == MaturityRate this reduces to: gamma = dt/UnlockRate * decay_x

// State update
if perpetual:
    locked_mass_new = locked_mass_old              // No decay
else:
    locked_mass_new = locked_mass_old * decay_x    // Exponential decay

conviction_new = decay_z * conviction_old + gamma * locked_mass_old
```

For locks against the subnet owner's hotkey, the formula simplifies to `conviction = locked_mass` (instant conviction, no roll-forward growth needed).

### Key Extrinsics

- `lock_stake(hotkey, netuid, amount)` — Lock alpha to a hotkey on a subnet (decaying by default).
- `set_perpetual_lock(netuid, perpetual: bool)` — Toggle between decaying (false) and perpetual (true) mode.
- `sudo_set_owner_cut_auto_lock_enabled(netuid, enabled: bool)` — Subnet-owner-only. Toggle whether owner-cut emissions are auto-locked.

### Key RPCs

- `get_coldkey_lock(coldkey, netuid) -> Option<LockState>` — **New in PR #2687.** Returns the live (rolled-forward) lock state for a given coldkey on a given subnet, including locked_mass, conviction, and last_update block. Single call gives you both balance and accrued conviction.
- `get_hotkey_conviction(hotkey, netuid) -> U64F64` — Aggregate conviction for a hotkey on a subnet.
- `get_most_convicted_hotkey_on_subnet(netuid) -> Option<AccountId>` — Returns the hotkey with the highest total conviction (i.e. the subnet-king candidate).

### Migration

Shipped with PR #2687:

- `migrate_reset_tnet_conviction_locks` — clears `Lock`, `HotkeyLock`, `DecayingHotkeyLock`, `OwnerLock`, `DecayingOwnerLock`, and `DecayingLock` storage on testnet. This wipes any pre-#2687 conviction state. Mainnet has not had v2 conviction live yet, so this migration is testnet-only in practice.

---

Analysis prepared by **Taostats** based on subtensor PRs #2658 and #2687 (#2687 merged to devnet-ready 2026-05-25, propagated to testnet same day).

This document is informational only.