---
title: How emission is determined
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

> 📘 **Where we are — step 1 of the emission flow**
>
> This is the start of the flow. See the [full emission flow](/docs/how-emission-works) for the whole chain.

Basics on how tao is emitted and distributed in Bittensor.

Every block, 0.5 tao is emitted by the chain (the first [Halving](/docs/halving) was in December 2025).  Where do these tokens go?

The tao is divided amongst the subnets based on emission.  And, then, depending on the alpha price, some is injected into the liquidity pool, and some is used as a chain buy to purchase alpha (that is held as protocol-owned alpha, not recycled).

As of spec 440 (2026-07-27), a subnet's share of per-block emission is **no longer proportional to demand**. Emission is now computed in two stages:

1. **Demand.** Each subnet's demand `s` is `subnet_moving_price × (1 − miner_burned)`, normalized across all subnets. (Before PR [#2800](https://github.com/opentensor/subtensor/pull/2800) this was also weighted by `root_proportion`; that weighting has been removed.) Until spec 440 this quantity *was* the emission share — now it is the **input** to the gate.
2. **The gate.** Demand feeds a Hill-function gate at a q-mass quantile bar θ: subnets above the bar keep ~all their share, the below-bar tail is choked toward zero, and the freed-up emission is redistributed up to the winners. Final emission is `eᵢ = sᵢ·gate(sᵢ) / Σⱼ sⱼ·gate(sⱼ)`.

Tao Flow / Net Tao Flow no longer drive emission. For the full derivation of the gate, the quantile bar, and the sudo knobs (`q`, `h`), see the canonical page: **[The emission gate (spec 440)](/docs/emission-gate)**. For how demand itself is built, see [Price-based subnet emission shares](/docs/price-based-emission-shares).

> 🚧 **Emission is not pro-rata to demand**
>
> Any APY or emission estimate that assumes a subnet earns emission *in proportion to* its price/demand is wrong as of spec 440. Above-bar winners are understated and the below-bar tail is overstated. See [The emission gate](/docs/emission-gate).

> 📘 **Historical**
>
> Between Nov 2025 and Jun 2026, emission shares were driven by tao flow (and later net tao flow). That mechanism was replaced on 2026-06-23 by the price-based shares + miner-burn scaling design, which spec 440 (2026-07-27) then turned into the *demand* input to the emission gate.

Emitted tao has 2 destinations:

* tao injected
* chain buy

## Tao injected

This is the primary feature of tao emission.  Tao from the chain is injected into the subnet's liquidity pool.  Alpha is minted and added at the same time (to keep the liquidity pool and the price balanced).

The alpha minted into the pool each block is capped at `root_proportion × alpha_emission`. Since `alpha_emission = 1` for all subnets currently, the de-facto per-block alpha cap is simply the subnet's `root_proportion`. Any TAO emission that can't be matched into the pool under this cap funds on-chain alpha buys instead (see Chain Buy below).

## Chain Buy

If alpha injection is limited by the cap, there is excess tao that was emitted to the subnet.  This tao is used to buy alpha; that alpha is not recycled — it is held in a protocol wallet and redistributed to alpha holders if the subnet is dissolved.  This mechanism raises the alpha price — eventually leading to the chain buys stopping.

> 📘 Example — Subnet 64
>
>   SN64 emits **0.05575 τ** this block (11.15% share × 0.5 τ). At a price of 0.0786 τ, that tao would mint **0.7093 α** if fully injected.
>
>   But SN64's `root_proportion` is **0.14605**, so the `alpha_in` cap is `0.14605 × 1 = 0.14605 α`. Since 0.7093 α ≫ 0.14605 α, injection is clamped to the cap:
>
>   * **Injected** (into the pool): 0.14605 α × 0.0786 τ = **0.01148 τ** (20.6% of emission)
>   * **Chain buy** (excess → market buy of alpha): **0.04427 τ** (79.4% of emission)

## What's next

**Step 2 — [Alpha emission](/docs/alpha-emission):** now that TAO has been emitted to each subnet, the subnet mints its own alpha per block, split into `alpha_in` (the pool) and `alpha_out` (1 α to participants).
