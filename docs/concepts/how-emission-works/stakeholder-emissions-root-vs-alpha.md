---
title: Calculating root proportion
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

> 📘 **Where we are — step 5 of the [emission flow](/docs/how-emission-works)**
>
> How we got here:
>
> 1. [TAO emission](/docs/tao-emission) — TAO split across subnets.
> 2. [Alpha emission](/docs/alpha-emission) — each subnet mints `alpha_in` + `alpha_out`.
> 3. [Split `alpha_out` among participants](/docs/split-alpha-out) — owner / miners / validators.
> 4. [Parent / child hotkeys](/docs/emission-parent-hotkeys) — aggregate each validator's dividends.
>
> **This page (step 5):** divide the validator's dividends into a root proportion and an alpha proportion.

In the Bittensor ecosystem, holders of tao may stake to a validator in a subnet in two different ways:

* **Root stake** : Staking to a validator in subnet 0, the root subnet.
* **Alpha Stake**: Staking to a validator in a subnet, exchanging your tao for alpha token.

<Image border={false} alt="Flow diagram of child/parent hotkey allocations entering a validator and a root:alpha split producing alpha-denominated local stake and tao-denominated root stake" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/011276c36ca5a252.png" />

The ratio of root: alpha staked is calculated using the `root_proportion`.

`root proportion` is calculated from 3 values:

* **tao on root**: The total amount of tao on root.
* **alpha issued**: The sum of `alpha_in` and `alpha_out` (all alpha emitted)
* **tao\_weight**: a variable set by the chain.  The current `tao_weight` is 0.18.

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/d9a8771680d608ca.png" />

## Current Root prop

Root proportion will change every block, as the tao and alpha values will have increased.  The results can be charted over time:

<Image border={false} alt="At day 0 there are 6M tao available." src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/33c9f8d3f656c2c1.jpg" />

The chart will vary on the amount of tao available at the moment the subnet is created. The above chart shows day 0 = 6 million tao.

On day 0 of the subnet, 100% of emission will go to root stakeholders.

50% root: 50% alpha is met at approximately day 70 (this is highly variable, and just an estimate).

> 📘 **Each Subnet has a statistics page showing the Root proportion chart for the subnet.**
>
> [https://beta.taostats.io/subnets/75/statistics](https://beta.taostats.io/subnets/75/statistics)

In this second chart, the yellow/green subnet is created 100 days after the blue/red subnet (9,720,000 tao, and 0 alpha for the 2nd subnet):

<Image border={false} alt="Line chart plotting root and alpha proportion (percent) versus time in days for two subnets, with the second pair time-shifted from the first" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/16a47e3932b78354.jpg" />

## What's next

The validator's dividends are now split into a root share and an alpha share. The final step distributes each to stakeholders:

* **Step 6a — [Stakeholder emissions: root](/docs/stakeholder-emissions-root)**
* **Step 6b — [Stakeholder emissions: alpha](/docs/stakeholder-emissions-alpha)**
