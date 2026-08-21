---
title: Root Subnet
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

The **root subnet** is netuid 0 — the coordinating subnet at the centre of Bittensor. Staking to root delegates TAO to root validators, whose weights across the other subnets determine how emissions flow through the network.

## Key points

* Root uses **only TAO** — there is no alpha token and no subnet-pool price risk.
* Root staking is the "safe" option, but root's share of total emissions [decreases over time by design](/docs/stakeholder-emissions-root-vs-alpha) as subnets mature.
* Under [Root Reborn](/docs/shorting-explainer), root dividends are handled through [validator baskets](/docs/root-validator-baskets) and redeemed with a manual `claim_root`.

## Related

* [Staking in dTao](/docs/staking-in-dtao)
* [Root Validator Baskets](/docs/root-validator-baskets)
* [Emissions: Root vs. Alpha Stake](/docs/stakeholder-emissions-root-vs-alpha)
