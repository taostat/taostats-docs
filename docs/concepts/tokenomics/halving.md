---
title: Halving
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

The [tokenomics](https://taostats.io/tokenomics) of Bittensor follow Bitcoin: when half of the remaining supply has been issued, emission halves.

Tao and alpha both halve, but on independent schedules because their per-block emissions differ.

> 📘 **Halvings are triggered by issuance, not block height**
>
> A halving fires when **total issuance** crosses the midpoint of the remaining supply (10.5M, then 15.75M, then 18.375M, ...) — it is not scheduled by block number. Because **recycled tao (e.g. registration burns) is subtracted from total issuance** and can be re-emitted, recycling pushes each halving *later*. Transaction fees are also **recycled** — subtracted from total issuance and available to be re-emitted — so, like registration recycling, they push halvings marginally later rather than being neutral.

## First halving (December 2025)

The first halving occurred in December 2025, when 10,500,000 tao had been issued. The block reward dropped by 50%.

* **tao**: per-block emission dropped from **1 → 0.5 τ/block** (December 2025).

> 📘 **The tao halving date can shift**
>
> Recycling removes tao from circulation, so the exact halving date cannot be predicted precisely. The first tao halving occurred in **December 2025**.

## Current per-block emissions (post-Dec-2025)

| Token | Per-block emission | Notes |
|-------|--------------------|-------|
| tao | 0.5 τ | halved Dec 2025 |
| alpha_out | 1 α | unchanged until alpha-side halving |

## Second halving

At 15.75M tao issued:

* **tao**: 0.5 → 0.25 τ/block

## Third halving

At 18.375M tao issued:

* **tao**: 0.25 → 0.125 τ/block

## etc.

> 📘 **The tao halving affects the timing of alpha halvings**
>
> Alpha added to the pool depends on the tao entering the pool. When tao halves, the tao entering each pool halves, which changes the slope of cumulative alpha emission. The tao halving is the yellow line in the chart below.
>
> The red dotted line marks 10.5M alpha — the first alpha-side halving threshold.
>
> <Image border={false} alt="Tao and alpha halving timeline" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/b68bfca83d7209cd.jpg" />

## See also

* [Alpha Emission](/docs/alpha-emission) — how alpha emission is calculated each block.
* [Tao Emission](/docs/tao-emission) — how 0.5 τ/block is distributed across subnets.
