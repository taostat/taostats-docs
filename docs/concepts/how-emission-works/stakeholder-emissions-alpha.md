---
title: Stakeholder emissions: alpha
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

Stakeholders may stake on a validator in a subnet.

* Staking on a subnet converts tao into subnet [Alpha Tokens](/docs/alpha-tokens).  This will cause there to the [Slippage](/docs/slippage)
* For every block, a percentage of emissions will be rewarded to each alpha stakeholder.

> 📘 **Where we are — step 6b of the [emission flow](/docs/how-emission-works)**
>
> How we got here:
>
> 1. [TAO emission](/docs/tao-emission) — TAO split across subnets.
> 2. [Alpha emission](/docs/alpha-emission) — each subnet mints `alpha_in` + `alpha_out`.
> 3. [Split `alpha_out` among participants](/docs/split-alpha-out) — owner / miners / validators.
> 4. [Parent / child hotkeys](/docs/emission-parent-hotkeys) — aggregate each validator's dividends.
> 5. [Root vs alpha split](/docs/stakeholder-emissions-root-vs-alpha) — divide dividends into root and alpha.
>
> **This page (step 6b):** distribute the **alpha** share to stakeholders.

## Emission in Alpha

<Image border={false} alt="Flow diagram of a validator's alpha emission passing through a root:alpha split into local and root stake, each divided between validator and stakeholders" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/ab80f9e8d345b952.png" />

Step 1: From the total dividends in alpha - deduct the validator's take, and award to their hotkey.

Step 2: With the remaining alpha, award every hotkey a weighted average (based on the amount of alpha stake)

## What's next

This is the final step of the emission flow — the alpha share has reached stakeholders as compounding subnet-alpha stake. To learn how to hold, add to, or unwind that position, see [Staking in dTao](/docs/staking-in-dtao) and [Price Impact and Slippage](/docs/slippage). See also the parallel path, [Stakeholder emissions: root](/docs/stakeholder-emissions-root).
