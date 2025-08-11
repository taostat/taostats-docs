---
title: Staking
excerpt: Learn about staking to root and alpha, and how these emissions are divided up.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
> 📘 Staking with taostats
>
> See [Staking Instructions](doc:staking-instructions) for a number of pages describing how to stake using Taostats.

<br />

Staking plays a principal role in the functioning of the Bittensor network. The principal goal of dTao is to divide chain emissions amongst subnets in a democratic way.  Staking into a subnet  increases the emissoins of the subnet.

# Subnet emission

Emission into a subnet is determined by the subnet price. (which is based on the amount of tao and alpha in the [Subnet Pool](doc:subnet-pools). The act of staking adds tao and removes alpha from the pool, increasing the price, and increasing emission to the subnet. Therefore subnet emission is guided by how much stake has been placed on the subnet.

# Staking Options

in dTao, there are two options for staking:

* [Staking to root](#staking-to-root)
* [Staking to a Subnet](#staking-to-alpha)

## Emission division: root to subnet

Stakeholder emission is split between these two options.  For new subnets, the emission is primarily to root, with subnet increasing over time

<Image align="center" alt="An example breakdown of root:subnet proportions." border={false} caption="An example breakdown of root:subnet proportions." src="https://files.readme.io/3e9d7b5c3747867d7b1d97a068bfceb15d003e0f4ba498f2f5b48bcca74f11ac-image.png" />

<br />

This change over time is described in [Emissions: Root vs. Alpha Stake](doc:stakeholder-emissions-root-vs-alpha).

## Staking to root

Staking to root does not affect subnet emissions, and is a `safe`  staking option - there is no way to lose tao value.   Root stakers earn a (ever decreasing) portion of returns from every subnet the validator is active in.

If you have staked to root, your returns will be auto-compounded to your hotkey on root.

## Staking to alpha

This is the new feature and primary goal of dTao - to enable stakeholders to vote and determine the emissions for every subnet.

To stake in alpha, tao is exchanged via the [Subnet Pools](doc:subnet-pools) into alpha.  This will incur [Slippage](doc:slippage). The received alpha is then staked to the validator selected.  Your returns will be in alpha, and autocompounded to the validator hotkey.

Staking to alpha *does* incur risk: a drop in alpha token price will result in a lower amout of tao when unstaking.

<br />

> 📘 Staking fees
>
> ## Root
>
> There is no fee to stake or unstake from root
>
> ## Subnets:
>
> * All staking and unstaking fees are default 0.05% of the stake/unstake value. This can be changed by the subnet owner. (the [Get Subnets](ref:get-subnets-1) API endpoint lists the `fee_rate`)

<br />

## Moving stake

The move stake command can be used to switch validators in a subnet.  Under the hood, this is an unstake, and then staking.  However, only one fee is charged.

<br />

## [dTao FAQ](doc:dtao-faq): Your top  staking questions