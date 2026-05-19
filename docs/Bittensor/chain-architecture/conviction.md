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

Technical Explainer  Based on subtensor PR #2658

## 1. What Is Conviction?

Conviction is Bittensor's governance mechanism that ties voting power to long-term commitment. When you lock alpha tokens to a subnet, you earn **conviction**  a measure of your stake's weight in governance decisions and subnet ownership.

Conviction exists to:

* Reward long-term alignment over short-term speculation

* Provide subnet governance stability

* Enable subnet ownership transitions through the "subnet king" mechanism

* Create skin-in-the-game for validators and subnet owners

Version 2 fundamentally redesigned the system: locks are now **perpetual by default**, subnet owners receive **instant conviction**, and the unlock queue was eliminated in favor of exponential decay.

## 2. How Locking Works

To earn conviction, you lock alpha tokens using the `lock_stake` extrinsic:

* **One lock per coldkey per subnet**  You can only have a single active lock targeting one hotkey on each subnet
* **Lock to a hotkey** Your locked alpha is associated with a specific hotkey on that subnet. This is typically the subnet owner's hotkey, or the hotkey of someone building conviction to challenge for subnet ownership.
* **Top-ups must match** Additional locks to the same subnet must target the same hotkey; you can't split locks across multiple hotkeys
* **Perpetual by default**  Locked mass stays constant indefinitely, allowing conviction to grow toward 100%
* **Optional decay** Use `set_perpetual_lock(false)` to enable exponential decay if you want to eventually unstake
  <br />
  <br />

## 3. Two Types of Locks

<br />

<br />

### Perpetual Locks (Default)

When you lock alpha without toggling decay, your lock is **perpetual**:

<br />

* `locked_mass` remains constant forever
* `conviction` grows exponentially from 0 toward `locked_mass`
* Conviction asymptotically approaches 99% after 1 year, 99.9%+ after 2 years
* Cannot unstake perpetual locks stay locked unless you toggle to decaying mode
  <br />

### Decaying Locks

After calling `set_perpetual_lock(false)`, your lock begins exponential decay:

<br />

* `locked_mass` decays with **UnlockRate** (158.6 day time constant)
* `conviction` follows a coupled decay/growth formula driven by **MaturityRate** (30.0 day time constant)
* After 365 days, 90% of locked mass has decayed (by design)
* You can unstake the difference between your original lock and current `locked_mass`
  <br />

### Subnet Owner Locks

Subnet owners receive special treatment:

<br />

* **Instant conviction**  `conviction` equals `locked_mass` immediately (no growth period)
* **Auto-locked owner cut** The owner's share of emissions is automatically locked each block, building conviction continuously
* Owner locks are perpetual by default but can opt into decay
  <br />
  <br />

## 4. The Numbers

<br />

<br />

### System Parameters

| Parameter             | Value (blocks) | Value (days) | Meaning                                                                                          |
| --------------------- | -------------- | ------------ | ------------------------------------------------------------------------------------------------ |
| **UnlockRate**        | 1,142,108      | 158.6 (tau)  | Time constant for locked mass decay. 90% decays in 365 days.                                     |
| **MaturityRate**      | 216,000        | 30.0 (tau)   | Time constant for conviction growth. 5.3Ã— faster than unlock rate. Half-life: 20.8 days.        |
| **Half-life (decay)** | ~792,000       | 110          | Time for locked mass to decay to 50% (decaying locks only). MaturityRate half-life is 20.8 days. |

### Conviction Growth Timeline (Perpetual Lock)

How conviction grows over time when `locked_mass` stays constant:

| Days Elapsed | Conviction (% of locked_mass) |
| ------------ | ----------------------------- |
| 0            | 0.0%                          |
| 7            | 20.8%                         |
| 14           | 37.3%                         |
| 30 (tau)     | 63.2%                         |
| 60           | 86.5%                         |
| 90           | 95.0%                         |
| 120          | 98.2%                         |
| 180          | 99.8%                         |
| 365          | ~100%                         |

### Locked Mass Decay Timeline (Decaying Lock)

How `locked_mass` decays after toggling `set_perpetual_lock(false)`:

| Days Elapsed    | Locked Mass Remaining |
| --------------- | --------------------- |
| 0               | 100.0%                |
| 30              | 82.8%                 |
| 60              | 68.5%                 |
| 90              | 56.7%                 |
| 110 (half-life) | 50.0%                 |
| 120             | 46.9%                 |
| 159 (tau)       | 36.8%                 |
| 365             | 10.0%                 |

## 5. Worked Example

<br />

**Scenario:** A validator locks 10,000 alpha on subnet 64 to their hotkey.

<br />

<br />

### Phase 1: Perpetual Lock (Default)

`locked_mass = 10,000 alpha` (constant)

| Time    | Conviction    | Can Unstake |
| ------- | ------------- | ----------- |
| Day 0   | 0 alpha       | 0 alpha     |
| Day 7   | 2,080 alpha   | 0 alpha     |
| Day 30  | 6,320 alpha   | 0 alpha     |
| Day 60  | 8,650 alpha   | 0 alpha     |
| Day 90  | 9,500 alpha   | 0 alpha     |
| Day 120 | 9,820 alpha   | 0 alpha     |
| Day 180 | 9,980 alpha   | 0 alpha     |
| Day 365 | ~10,000 alpha | 0 alpha     |

**Note:** Perpetual locks cannot be unstaked. Locked mass stays at 10,000 alpha forever.

### Phase 2: Toggle to Decaying

At day 365, the validator calls `set_perpetual_lock(false)`. Now both `locked_mass` and `conviction` evolve:

| Days Since Toggle | Locked Mass | Conviction | Can Unstake |
| ----------------- | ----------- | ---------- | ----------- |
| 0                 | 10,000      | 9,900      | 0           |
| 30                | 8,280       | 8,530      | 1,720       |
| 60                | 6,850       | 7,280      | 3,150       |
| 90                | 5,670       | 6,160      | 4,330       |
| 120               | 4,690       | 5,180      | 5,310       |
| 159 (tau)         | 3,680       | 4,090      | 6,320       |
| 365               | 1,000       | 1,090      | 9,000       |

**Unstakeable amount** = original lock (10,000) âˆ’ current `locked_mass`

After 1 year of decay, the validator can unstake 9,000 alpha, leaving 1,000 still locked.

## 6. Subnet Owner Locks

Subnet owners accumulate locked alpha automatically and receive immediate conviction:

<br />

* **Owner cut auto-locked:** Each block, the owner's emissions share is locked to their subnet ownership hotkey
  * **No initial alpha distribution:** In v2, subnet registration does not distribute initial alpha to the owner. Conviction builds solely through the auto-locked owner cut from ongoing emissions.
    * **Instant conviction:** Unlike validators, owners don't wait for conviction to grow  `conviction = locked_mass` immediately
      * **Perpetual by default:** Owner locks don't decay unless the owner explicitly calls `set_perpetual_lock(false)`
        * **Aggregate tracking:** All owner locks on a subnet are aggregated into `OwnerLock` storage for subnet king calculations

          <br />

          This instant conviction ensures subnet owners always have governance weight proportional to their locked stake without waiting periods.

          <br />

## 7. Subnet King Mechanism

**Note: The subnet king mechanism is currently disabled by design.** The code exists but the ownership-transfer call is commented out. When enabled, the rules would be:

<br />

After a subnet has been active for **1 year** (365.25 days), ownership could transfer via the "subnet king" mechanism:

<br />

### Eligibility Requirements

* Subnet must be at least 365.25 days old
* Total rolled conviction across the **entire subnet** (all hotkeys, all coldkeys, including owner) must be at least **10% of SubnetAlphaOut**. This is a subnet-wide gate, not per-challenger.
* The **hotkey** with the highest aggregate conviction wins. Conviction is aggregated per hotkey (from all coldkeys locking to that hotkey), not per coldkey.
  <br />

### How It Works

* **Aggregate calculation:** The system sums conviction across all locks (owner + non-owner) for each coldkey
* **Comparison:** The hotkey with the highest total conviction (summed from HotkeyLock + DecayingHotkeyLock + OwnerLock) becomes the subnet king.
* **Transfer:** Ownership transfers, and the lock aggregates swap:
  <br />
  Old owner's `OwnerLock` â†’ becomes non-owner locks
  * New owner's non-owner locks â†’ become `OwnerLock`

    <br />
  * **Instant conviction retained:** The new owner keeps their conviction value but now has instant-conviction status for future locks

    <br />

    **Design rationale:** This mechanism prevents permanent ownership monopolies while requiring challengers to demonstrate long-term commitment through locked alpha and conviction growth.

    <br />

## 8. What You Can and Can't Do

<br />

<br />

### Allowed Actions

* **Top up existing lock:** Add more alpha to your existing lock (must target the same hotkey)
* **Move lock to a different hotkey:** You can move your lock to a different hotkey on the same subnet. If the destination hotkey is owned by the _same coldkey_, conviction is preserved. If owned by a _different coldkey_, conviction resets to zero.
* **Toggle decay mode:** Switch between perpetual and decaying at any time with `set_perpetual_lock`
* **Partial unstaking (decaying only):** Unstake the difference between original lock and current `locked_mass`
  <br />

### Not Allowed

* **Unstake perpetual locks:** You must first toggle to decaying mode and wait for mass to decay
* **Cross-subnet transfers:** Locks are subnet-specific and cannot be moved between subnets
* **Multi-hotkey locks:** You cannot have multiple locks to different hotkeys on the same subnet from one coldkey
* **Lock hotkey changes:** If you have an active lock on a subnet, you can't lock to a different hotkey without first removing the existing lock
* **Coldkey swap with active locks on destination:** A coldkey swap requires the destination coldkey to have **no active locks**. The source coldkey's locks transfer to the destination, but only if the destination is clean.
  <br />
  <br />

## 9. Technical Reference

<br />

<br />

### Storage Maps

| Storage                              | Key                       | Value     | Purpose                                                                                                         |
| ------------------------------------ | ------------------------- | --------- | --------------------------------------------------------------------------------------------------------------- |
| `Lock`                               | (coldkey, netuid)         | LockState | Legacy/compatibility tracks basic lock state                                                                    |
| `HotkeyLock(netuid, hotkey)`         | (coldkey, netuid, hotkey) | LockState | Aggregate conviction from all perpetual (non-decaying) non-owner coldkeys locking to this hotkey on this subnet |
| `DecayingHotkeyLock(netuid, hotkey)` | (coldkey, netuid, hotkey) | LockState | Aggregate conviction from all decaying non-owner coldkeys locking to this hotkey on this subnet                 |
| `OwnerLock(netuid)`                  | (coldkey, netuid)         | LockState | Aggregate conviction for the subnet owner coldkey's lock on this subnet                                         |
| `DecayingLock(coldkey, netuid)`      | (coldkey, netuid)         | LockState | Per-coldkey flag: when present, that coldkey's lock decays. Missing = perpetual.                                |

### LockState Structure

```
```

```
 LockState {
 locked_mass: u64, // Current locked alpha (decays if non-perpetual)
 conviction: u64, // Governance weight (grows/decays based on mode)
 last_update: u64 // Block number of last state update
}
```

### Roll-Forward Formula

When reading lock state, the system rolls forward from `last_update` to the current block:

<br />

```

<br />

// Time elapsed in blocks
dt = current_block - last_update

<br />

// Decay factors
decay_x = exp(-dt / UnlockRate) // = exp(-dt / 1,142,108)
decay_z = exp(-dt / MaturityRate) // = exp(-dt / 216,000)

<br />

// Coupling factor
gamma = UnlockRate Ã— (decay_x - decay_z) / (UnlockRate - MaturityRate)

<br />

// State update
if perpetual:
locked_mass_new = locked_mass_old // No decay
else:
locked_mass_new = locked_mass_old Ã— decay_x // Exponential decay

<br />

conviction_new = decay_z Ã— conviction_old + gamma Ã— locked_mass_old

<br />


```

<br />

For subnet owners with instant conviction, the formula simplifies to `conviction = locked_mass` (no roll-forward needed for conviction growth).

<br />

### Key Extrinsics

<br />

* `lock_stake(hotkey, netuid, amount) Lock alpha to a hotkey on a subnet (perpetual by default)
  * `set_perpetual_lock(netuid, perpetual: bool) Toggle between perpetual (true) and decaying (false) mode
