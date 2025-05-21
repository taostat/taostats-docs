---
title: 'Stakeholder Emissions: Alpha'
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
Stakeholders may stake on a validator in a subnet.  

- Staking on a subnet converts tao into subnet [Alpha Tokens](doc:alpha-tokens).  This will cause there to the [Slippage](doc:slippage)
- For every block, a percentage of emissions will be rewarded to each alpha stakeholder.

> 📘 How we got to this step of Emission:
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

## Emission in Alpha

![](https://files.readme.io/61749ce2da0bc241cb78511c460abb2c6eff910402ebba1c57719440d4353feb-image.png)

<br />

Step 1: From the total dividends in alpha - deduct the validator's take, and award to their hotkey.

Step 2: With the remaining alpha, award every hotkey a weighted average (based on the amount of alpha stake)