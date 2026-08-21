---
title: Subnet deregistration
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

When a subnet is deregistered, its entire TAO reserve is drained and paid out pro-rata by alpha across everyone with a claim on the pool. TAO you receive lands in your coldkey free balance.

Since runtime 415 (subtensor v3.4.2-415), not all of that TAO reaches stakers. A portion is withheld from the pool and recycled (removed from circulation), and that portion is baked into the per-alpha payout you see as the subnet's liquidation price on [taostats.io/subnets](https://taostats.io/subnets).

## The deregistration → registration timeline

Deregistration and the registration that triggers it happen close together but are distinct on-chain events:

1. **Block *x* — the old subnet is dissolved.** The chain drains the subnet's entire `SubnetTAO` pot and computes each holder's share (see [What actually happens](#what-actually-happens-on-deregistration) below). All alpha holdings are effectively sold at the liquidation price.
2. **Blocks between *x* and *y* — TAO is paid out.** Each holder's TAO share is transferred from the subnet's protocol address to their coldkey free balance. These land as ordinary `Balances.transfer` events from the protocol address.
3. **Block *y* — the new subnet is created.** The incoming registration that pushed the subnet count over the cap takes the freed netuid slot.

## Two ways to find the TAO a holder received

**Method 1 — map the transfer events (empirical).** Walk every `Balances.transfer` event out of the subnet's protocol address from block *x* to block *y* and sum the amounts to each coldkey. This is the ground truth of what actually landed, and Taostats indexes these transfers via the [events API](/docs/events-detail). Use this when you want the exact figure a specific coldkey received.

**Method 2 — compute from the liquidation price (analytical).** Multiply the holder's alpha by the liquidation price. This reconstructs the same number from chain state without walking events:

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/364e6dc1eb2f601f.png" />

where the liquidation price depends on when the subnet was registered:

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/e5fa3c7398ff22e9.png" />

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/ae02bebc5d1d8919.png" />

$\alpha_{staked}$ is the sum of every staker's actual alpha (per hotkey, per coldkey share-pool value). $\alpha_{protocol}$ is `SubnetProtocolAlpha`; $\alpha_{in}$ is `SubnetAlphaIn`. The gate block 8,334,450 is `TaoInRefundDeploymentBlock` on finney. Method 2 matches Method 1 for staker payouts; it will not show the withheld protocol/pool-reserve slice, because that TAO is recycled rather than transferred to anyone.

## When does a subnet get deregistered?

For a subnet to be deregistered, it must be:

1. Out of immunity (subnets have 4 months of immunity from registration).
2. The lowest-priced subnet at the time a new registration would push the count over the cap.

If two subnets tie on the lowest price, the older one is deregistered.

## Who has a claim on the pool

At deregistration, the total alpha the TAO pot is divided against is the sum of:

- Every staker's alpha (per hotkey, per coldkey).
- `SubnetProtocolAlpha` — protocol-owned alpha accumulated from per-block chain buys. Always included.
- `SubnetAlphaIn` — the AMM pool-reserve alpha paired against `SubnetTAO`. Included for new subnets only (see the gate below).

Three distinct pools of alpha share the denominator:

**Staker alpha.** Alpha you hold, tracked in per-(hotkey, coldkey) share pools. Always in the denominator; stakers get their pro-rata TAO share into their coldkey free balance.

**Protocol alpha (`SubnetProtocolAlpha`).** Alpha the protocol accumulates from per-block chain buys. Always in the denominator; its TAO share is not paid out — it is recycled.

**Pool-reserve alpha (`SubnetAlphaIn`).** The AMM reserve alpha paired against `SubnetTAO`. In the denominator for new subnets only; its TAO share is also recycled.

### Where `SubnetProtocolAlpha` comes from

Each block, a subnet's excess TAO is swapped TAO to alpha by the coinbase. Before runtime 415 that chain-bought alpha was recycled immediately. Since runtime 415, it is retained in `SubnetProtocolAlpha` and only settled at deregistration.

## Legacy vs. new subnets

Whether `SubnetAlphaIn` is included in the denominator depends on when the subnet was registered:

- If the subnet was registered after `TaoInRefundDeploymentBlock`, it is a new subnet: the denominator includes `SubnetAlphaIn` and `SubnetProtocolAlpha`.
- Otherwise it is a legacy subnet: the denominator includes `SubnetProtocolAlpha` only.

`TaoInRefundDeploymentBlock` was stamped at the block runtime 415 activated. On finney it is block 8,334,450.

Both legacy and new subnets distribute `SubnetProtocolAlpha`. The gate only toggles pool-reserve alpha.

Not to be confused with `NetworkRegistrationStartBlock` (6,573,966), which governs the owner lock-cost refund path — a separate mechanism described below.

## What actually happens on deregistration

When the chain dissolves a subnet, it:

1. Finalizes root dividends for the subnet.
2. Computes the total alpha denominator using the rules above.
3. Removes the full `SubnetTAO` pot from the subnet and from `TotalStake`.
4. Splits the pot pro-rata using the largest-remainder method. Each staker's share goes to their coldkey free balance. The `SubnetProtocolAlpha` share (and `SubnetAlphaIn` share on new subnets) is accumulated into an internal protocol TAO share and is not paid to any staker.
5. Destroys all per-key alpha, hotkey share-pool totals, and the `SubnetAlphaIn`, `SubnetAlphaOut`, and `SubnetProtocolAlpha` counters.
6. Applies the owner lock refund on legacy subnets registered before `NetworkRegistrationStartBlock`. The refund is `max(0, lock_cost − owner_received_emission_in_tao)` and cannot draw from the withheld protocol TAO share.
7. Recycles any TAO left on the subnet account — including the withheld protocol TAO share — via `recycle_tao`. That TAO is burned back and recorded in `RAORecycledForRegistration`.
8. Clears the remaining subnet storage (params, weights, emissions, locks, token symbol, mechanism) and emits `NetworkRemoved`.

## Why per-alpha payout is lower than "pot divided by staker alpha"

The protocol's alpha stays in the denominator on purpose. It dilutes the per-alpha payout so the number you see reflects that some of the pot leaves the holder pool entirely.

Worked example. Suppose at deregistration a subnet has `SubnetTAO = 100 τ` and:

- Stakers hold 70 alpha in total.
- Protocol alpha (`SubnetProtocolAlpha` plus `SubnetAlphaIn` where applicable) is 30 alpha.
- Total denominator is 100 alpha.

Then:

- Per-alpha price is 100 τ / 100 alpha = 1 τ per alpha.
- Stakers collectively receive 70 × 1 = 70 τ, split by individual alpha.
- The protocol's 30 τ slice is withheld and recycled — it does not reach stakers.

Dividing 100 τ by only the 70 staker alpha would give 1.43 τ per alpha and overstate every holder's payout by about 43%. The live liquidation price shown on each [subnet page](https://taostats.io/subnets) already accounts for the full denominator.

**New subnets** (registered after block 8,334,450):

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/f9786741278b54aa.png" />

**Legacy subnets** (registered at or before block 8,334,450):

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/085e98d27b5cc721.png" />

Here $\alpha_{staked}$ is the sum of every staker's actual alpha share-pool value (summed per hotkey, per coldkey at dissolve) — **not** the `SubnetAlphaOut` issuance counter, which the payout math does not use. $\alpha_{protocol}$ is `SubnetProtocolAlpha` and $\alpha_{in}$ is `SubnetAlphaIn`. Your own payout is $\text{liq price} \times \text{your }\alpha$.

## Liquidation price vs. market price

The liquidation price is the effective per-alpha TAO you receive from draining the pool, after the denominator dilution above.

- If the liquidation price is above the current market price, holders are paid a premium versus market.
- If it is below, holders take a loss versus market.

Live liquidation prices are on each subnet page at [taostats.io/subnets](https://taostats.io/subnets).

## Storage items involved

- `SubnetTAO` — TAO reserve in the subnet. This is the pot distributed at deregistration.
- `SubnetProtocolAlpha` — protocol-owned alpha accumulated from per-block chain buys (runtime 415 and later).
- `SubnetAlphaIn` — AMM pool-reserve alpha paired against `SubnetTAO`.
- `SubnetAlphaOut` — alpha issuance tracker (staked-out alpha). Not used in the liquidation-price denominator; the payout math sums actual staker share-pool alpha instead.
- `TaoInRefundDeploymentBlock` — cutover block for the new denominator rule. On finney: 8,334,450.
- `NetworkRegisteredAt` — the block a subnet was registered. Determines legacy vs. new.
- `NetworkRegistrationStartBlock` — 6,573,966. Determines eligibility for the owner lock-cost refund.

## Source

This behaviour is defined in `pallets/subtensor/src/staking/remove_stake.rs::destroy_alpha_in_out_stakes` and `pallets/subtensor/src/coinbase/root.rs::do_dissolve_network` in the [opentensor/subtensor](https://github.com/opentensor/subtensor) repository, spec_version 425. The relevant runtime is v3.4.2-415, published in commits d1de05615 and f40f4ae6f.
