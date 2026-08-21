---
title: tao and alpha emissions
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

> 📘 **Current emission basis**
>
> This page describes the live, on-chain behavior after PRs [#2779](https://github.com/opentensor/subtensor/pull/2779) and [#2781](https://github.com/opentensor/subtensor/pull/2781) (merged 2026-06-23), as modified by the **spec 440 emission gate** (2026-07-27). The price-based quantity below is now the *demand* input to the gate, not the final share — see [The emission gate](/docs/emission-gate) and [Price-based emission shares](/docs/price-based-emission-shares).

Every block, each emit-enabled subnet receives a share of TAO emission and mints alpha. The flows are:

* **`tao_in`** — TAO emitted into the subnet pool, set by the price-based shares formula.
* **`alpha_in`** — alpha added to the subnet pool, set by `min(tao_emission/price, root_proportion × alpha_emission)`.
* **`alpha_out`** — alpha distributed to subnet stakeholders.

See also: [Tao Emission Distribution](/docs/tao-emission), [Alpha Emission](/docs/alpha-emission).

# `tao_in`

`tao_in` is the TAO that flows into the subnet's liquidity pool each block. It is **not** the subnet's full TAO emission — that emission splits between `tao_in` (pool injection) and on-chain alpha buys. The combined share each subnet receives is set in two stages. First the chain computes each subnet's **demand**:

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/a63b824a5db6690e.png" />

renormalized across all emit-enabled subnets. As of **spec 440**, this demand is *not* the emission share — it feeds a **Hill-function gate** at a quantile bar θ that boosts above-bar subnets and chokes the below-bar tail toward zero, then renormalizes:

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/c19b0b46436e0479.png" />

`tao_in` is the slice of the **gated** emission that lands in the pool; the remainder funds on-chain alpha buys (see [Tao Emission](/docs/tao-emission) for the chain-buy path).

* **`price_i`** — the subnet's `SubnetMovingPrice` exponential moving average, normalized across emit-enabled subnets.
* **`(1 − miner_burned_i)`** — penalty for subnets that routed last tempo's miner emission to owner or owner-immune hotkeys. Applies whether the withheld emission was burned or recycled.
* **`gate(s_i)`** — the spec 440 emission gate. See [The emission gate](/docs/emission-gate) for θ, `h`, `q`, and the redistribution.

If the weighted demand sum is zero (all subnets at full burn), the chain falls back to raw normalized `price` shares and emission still flows.

See: [The emission gate](/docs/emission-gate) for the gate, and [Price-based emission shares](/docs/price-based-emission-shares) for how demand is built.

# `alpha_in`

`alpha_in` is the alpha added to the subnet pool each block:

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/cdad5ad7b9d5f86c.png" />

where `tao_emission_i` is the subnet's per-block TAO emission, `price_i` is the pool's current alpha price in TAO, and `alpha_emission` is the base alpha mint per block (≤ 2, subject to halving). The cap is `root_proportion × alpha_emission`; the first term is the alpha you'd get by injecting the full TAO emission at the current pool price. The smaller of the two is what enters the pool.

Any TAO that doesn't get matched into the pool funds on-chain alpha buys instead — see [Tao Emission](/docs/tao-emission). For subnets with low `root_proportion` (older subnets with significant alpha issuance), most fresh alpha enters circulation via chain buys rather than direct pool injection.

See: [Alpha Emission](/docs/alpha-emission) for the alpha-supply schedule.

# `alpha_out`

Every block, `alpha_out` (the per-block alpha distributed to subnet stakeholders) is distributed amongst stakeholders according to the subnet's incentive distribution.

For the full walkthrough of how `alpha_out` is split across miners, validators, and stakeholders, see [Subnet Emissions (Alpha)](/docs/split-alpha-out).
