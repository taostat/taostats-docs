---
title: Alpha emission
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

> 📘 **Where we are — step 2 of the [emission flow](/docs/how-emission-works)**
>
> How we got here:
>
> 1. [TAO emission](/docs/tao-emission) — TAO split across subnets, injected into pools + chain buys.
>
> **This page (step 2):** each subnet mints its own alpha per block — `alpha_in` (pool) and `alpha_out` (participants).

Each subnet emits alpha every block through **two distinct pathways**, which serve different purposes:

* **`alpha_in`** — alpha injected into the subnet's liquidity pool (paired with tao), which sets the pool price and depth. When the pool injection is capped, the leftover tao becomes a **chain buy** instead. Capped at `root_proportion × alpha_emission` per block (de-facto the subnet's `root_proportion`, since `alpha_emission = 1`). See [Tao Emission](/docs/tao-emission) for the chain-buy mechanic.
* **`alpha_out`** — alpha paid out to the subnet owner, miners, validators, and stakers. A flat 1 α/block, distributed via the incentive split — see [Subnet emission overview](/docs/split-alpha-out).

`alpha_in` and `alpha_out` are governed by independent rules and currently halve on different schedules. See [Halving](/docs/halving) for the full schedule.

## alpha_in (capped at root_proportion × alpha_emission)

Each block, the chain injects tao into the subnet pool and mints a matching amount of alpha to keep the pool's tao : alpha ratio balanced.

The alpha injected is the smaller of two quantities: the tao injected divided by the current alpha price, and the per-block cap `root_proportion × alpha_emission`:

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/be4dc6a20f739a9a.png" />

Since `alpha_emission = 1` for all subnets currently, the cap is de-facto the subnet's `root_proportion`.

Below the cap, the injected alpha is simply the injected tao valued at the current alpha price:

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/7d67a97f8d58901a.png" />

> 📘 **Cap: alpha_in ≤ root_proportion × alpha_emission**
>
> If `tao_injected / alpha_price` would exceed `root_proportion × alpha_emission`, the `tao_injected` is reduced until `alpha_in` equals the cap. The leftover tao becomes a **chain buy** — the chain buys alpha from the pool. The alpha purchased this way is **not recycled**; it is held in a protocol wallet and redistributed to alpha holders if the subnet is dissolved. See [Tao Emission](/docs/tao-emission) for the full mechanic.
>
> (This cap was previously a flat 0.5 α/block. As of subtensor PR [#2779](https://github.com/opentensor/subtensor/pull/2779) the `alpha_in` cap is `root_proportion × alpha_emission`.)

## alpha_out (1 α/block)

`alpha_out` is a flat 1 α emitted per block per subnet, distributed to the subnet owner, miners, validators, and stakers via the standard incentive split. It is **not** affected by the December 2025 tao halving.

`alpha_out` will halve on its own schedule, when 10.5M alpha have been issued in that subnet — see [Halving](/docs/halving).

To learn how this 1 α is split across participants, see [Subnet emission overview](/docs/split-alpha-out).

## Worked example — Subnet 64

SN64 has emission share 11.15%, alpha price 0.0786 τ, and `root_proportion` 0.14605 (so the `alpha_in` cap is `0.14605 × 1 = 0.14605 α`).

* tao emitted to this subnet: 11.15% × 0.5 τ = **0.05575 τ**
* alpha this tao would mint at price: 0.05575 / 0.0786 = **0.7093 α** (far exceeds the 0.14605 α cap)
* alpha_in this block: **0.14605 α** (clamped to the `root_proportion` cap)
* tao actually injected: 0.14605 × 0.0786 = **0.01148 τ** (20.6% of emission)
* excess tao → chain buy (alpha held in protocol wallet): **0.04427 τ** (79.4% of emission)
* alpha_out this block: **1 α** (unchanged)

Total alpha entering the subnet ecosystem this block: 0.14605 α (`alpha_in`) + 1 α (`alpha_out`) = **1.14605 α**.

## What's next

**Step 3 — [Split `alpha_out` among participants](/docs/split-alpha-out):** the 1 α/block of `alpha_out` is divided among the subnet owner (18%), miners (41%), and validators (41%).

## See also

* [Halving](/docs/halving) — current emission ceilings and the halving schedule.
* [Tao Emission](/docs/tao-emission) — how 0.5 τ/block is split into pool injection and chain buys, and what happens to chain-buy alpha (held in protocol wallet, redistributed on subnet dissolution).
* [Subnet emission overview](/docs/split-alpha-out) — how `alpha_out` is distributed across owner, miners, validators, and stakers.
