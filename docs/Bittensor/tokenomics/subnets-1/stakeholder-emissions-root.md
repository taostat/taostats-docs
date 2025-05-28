---
title: 'Stakeholder Emissions: Root'
excerpt: updated Feb 3
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
> 📘 How we got to this step of Emissions
>
> Step 1: [Subnet Emission Distribution](doc:subnet-emissions): How emitted tao is split amongst the subnets
>
> Step 2: [Alpha Emission](doc:alpha-emission): How the emitted alpha is split between the Subnet pool and subnet participants.
>
> Step 3: [Emissions for Validators](doc:incentive-for-validators): How the Subnet emission is divided amongst all the validators.
>
> Step 4: [Emission for Parent/Child Hotkeys](doc:emission-parent-hotkeys): On each subnet, determine the rewards for each validator. This sums across all parent and child hotkeys.  The validator's take is removed.
>
> Step 5: [Emissions: Root vs. Alpha Stake](doc:stakeholder-emissions-root-vs-alpha): Divide the validator's dividends into a root proportion and an alpha proportion

# Root Emissions:

Stakeholders on root place their delegation of tao on a root validator.

* For every subnet the validator is active: stakeholders will earn a proportion of the rewards.
* Root staking will have lower returns over time, as stakeholder emission is split between alpha and root stakeholders (see [Emissions: Root vs. Alpha Stake](doc:stakeholder-emissions-root-vs-alpha)
* Every block, all root emissions will be sold from alpha to tao, and the tao will be auto-compounded - added to the existing stake on root.

![](https://files.readme.io/2da8bf7e761df3ea8a40dbe193160a4891dfd6a0328d3afc116c673afba4db40-image.png)

> 📘 Pre- dTao analogy
>
> Pre-dTao, staking was done to a validator.
>
> * Rewards were earned across all subnets the validator was active.
>
> dTao: this is staking to a validator on root.

<br />

# Calculating Root Emission

Step 1:  The validator take is removed from the root emission and awarded to the validator's hotkey. The validator's emission can either be swapped to root, or staked as alpha on the subnet.

Step 2: The total root tao for stakeholders is divided as a weighted average amongst all stakeholders based on the amount of root stake and added to their hotkey.