---
title: Root Emissions:
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

> 📘 **Where we are — step 6a of the [emission flow](/docs/how-emission-works)**
>
> How we got here:
>
> 1. [TAO emission](/docs/tao-emission) — TAO split across subnets.
> 2. [Alpha emission](/docs/alpha-emission) — each subnet mints `alpha_in` + `alpha_out`.
> 3. [Split `alpha_out` among participants](/docs/split-alpha-out) — owner / miners / validators.
> 4. [Parent / child hotkeys](/docs/emission-parent-hotkeys) — aggregate each validator's dividends.
> 5. [Root vs alpha split](/docs/stakeholder-emissions-root-vs-alpha) — divide dividends into root and alpha.
>
> **This page (step 6a):** distribute the **root** share to stakeholders.

Stakeholders on root place their delegation of tao on a root validator.

* For every subnet the validator is active: stakeholders will earn a proportion of the rewards.
* Root staking will have lower returns over time, as stakeholder emission is split between alpha and root stakeholders (see [Emissions: Root vs. Alpha Stake](/docs/stakeholder-emissions-root-vs-alpha)
* Every block, root dividends are sold from alpha to tao. Since **[Root Reborn](/docs/shorting-explainer)** (mainnet, `spec_version` 441) they are **not** auto-compounded onto your root stake — instead they are re-bought across your validator's basket and held until you make a manual `claim_root`. See [Root Validator Baskets](/docs/root-validator-baskets).

<Image border={false} alt="Flow diagram of validator emissions through a root:alpha split, with the tao-denominated root-stake branch highlighted and each branch split by commission between validator and stakeholders" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/e970ce18bf6e1ae3.png" />

> 📘 **Pre- dTao analogy**
>
> Pre-dTao, staking was done to a validator.
>
> * Rewards were earned across all subnets the validator was active.
>
> dTao: this is staking to a validator on root.

# Calculating Root Emission

Step 1:  The validator take is removed from the root emission and awarded to the validator's hotkey. The validator's emission can either be swapped to root, or staked as alpha on the subnet.

Step 2: The total root tao for stakeholders is divided as a weighted average amongst all stakeholders based on the amount of root stake and added to their hotkey.

## What's next

This is the final step of the emission flow — the root share has reached stakeholders. Under **Root Reborn** these rewards accrue to your validator's basket and are realized on a manual `claim_root`; see [Root Validator Baskets](/docs/root-validator-baskets) and [Staking in dTao](/docs/staking-in-dtao). See also the parallel path, [Stakeholder emissions: alpha](/docs/stakeholder-emissions-alpha).
