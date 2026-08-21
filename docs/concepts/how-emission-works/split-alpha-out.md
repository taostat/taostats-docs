---
title: Split alpha_out (owner / miners / validators)
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

> 📘 **Where we are — step 3 of the [emission flow](/docs/how-emission-works)**
>
> How we got here:
>
> 1. [TAO emission](/docs/tao-emission) — TAO split across subnets.
> 2. [Alpha emission](/docs/alpha-emission) — each subnet mints `alpha_in` + `alpha_out`.
>
> **This page (step 3):** split the 1 α/block of `alpha_out` among the subnet owner, miners, and validators.

This page shows how a subnet's `alpha_out` is divided among participants, then points to the rest of the flow.

<Image border={false} alt="Cascading flow diagram of one alpha emission split among subnet owner, validators, and miners, then through hotkey allocations and a root:alpha stake split to validator and stakeholders" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/4c1130c9de241de0.png" />

## The `alpha_out` split (1 α/block)

* **Subnet owners** receive **18%** of subnet emission.
* **[Miners](/docs/consensus-for-miners)** receive **41%** of emissions.
* **[Validators](/docs/dividends-for-validators)** receive **41%** of emissions — which is then further divided amongst their stakeholders (steps 4–6).

## What's next

**Step 4 — [Parent / child hotkeys](/docs/emission-parent-hotkeys):** aggregate each validator's dividends across its parent and child hotkeys. Then:

* Step 5: [Root vs alpha split](/docs/stakeholder-emissions-root-vs-alpha) — divide the validator's dividends into root and alpha proportions.
* Step 6: award stakeholder rewards — [root](/docs/stakeholder-emissions-root) and [alpha](/docs/stakeholder-emissions-alpha).
