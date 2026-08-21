---
title: Tao Flow
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

> 🚧 **Superseded — 2026-06-23**
>
> Tao Flow and Net Tao Flow no longer drive subnet emission shares. As of 2026-06-30 (subtensor PRs [#2779](https://github.com/opentensor/subtensor/pull/2779), [#2781](https://github.com/opentensor/subtensor/pull/2781), and [#2800](https://github.com/opentensor/subtensor/pull/2800), live on chain), emission shares are proportional to `subnet-price EMA × (1 − miner_burned)`, renormalized across subnets. (#2800 removed the earlier `root_proportion` weighting from the share formula.)
>
> See the canonical page: [Price-based subnet emission shares](/docs/price-based-emission-shares).
>
> This page is kept for historical context. Tao flow remains a useful stakeholder-activity metric (staking in/out of the subnet pool), but it is no longer an input to the emission equation.

As of May 2026, there are two types of tao flow.  The article attempts to first disambiguate them and then define them, and their uses.

Introduced in November 2025, tao flow is the measurement of staking and unstaking through the subnet liquidity pool.  Its original use was to determine the emissions of a subnet.  This changed in May 2026, with the introduction of Net Tao Flow.

Tao flow is still an interesting figure - it is a measure of how stakeholders are entering and exiting the subnet.

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/13fd503e4273b898.png" />

# Net Tao Flow

Introduced in May 2026 to counteract issues with tao flow.  The principal issue is that while tao flow is a good metric, it does not account for subsidies from the chain.  A new term, Protocol cost is added.

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/43a3d5a15e62480f.png" />

If netTaoFlow {'<0'}, it is set at 0 - there is no concept of negative emission.

But to smooth these values, a 30 day [exponential moving average](#/concepts/legacy-deprecated/tao-flow/#exponential--moving-average-example) is used for both.

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/2e69fd1766d51271.png" />

This new term is used to define the emissions delivered to a subnet.

## Protocol cost

Each block, the subnet is subsidized by [Tao Emission ](/docs/tao-emission) - broken into Tao injected into the pool and chain buys.  Root sells of alpha work in the opposite direction: when validators claim and swap their root‑alpha dividends, TAO leaves the pool, offsetting part of the subsidy.

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/9f33cf3b8ee29bcf.png" />

### Exponential  Moving Average example

To smooth this equation, each subnet's flow is placed in an exponential moving average with a half life of 30 days:

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/a7593596477af902.png" />

This video explains the launch of tao flow:

# Flow based emission

Starting in November 2025, tao flow will begin to be a part of the tao emission equation. By December 2025, 100% of tao emitted will be based on tao flow.

## What is flow

In every subnet, tao flows in and out of the liquidity pool through staking actions:

Flow is *only staking* it is **NOT** based on emission, root proportion or neuron registration.We can then normalize the flows across all subnets:

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/7e10c8e23f3fdb90.png" />

> 📘 Note: this is the default tao\_in.  The actual tao in *may* be smaller than this due to [Tao Excess](/docs/tao-emission-does-not-add-to-100).  This occurs when price and default tao emission result in "too much" alpha\_in injected into the pool.
>
>   The alpha\_in is scaled to it's maximum emission, which results in scaling down the tao\_in.  The difference is called excess tao.
