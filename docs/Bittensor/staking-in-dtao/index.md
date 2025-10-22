---
title: Staking
excerpt: Staking tao/alpha is how investors earn yield.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
<Callout icon="📘" theme="info">
  # Staking with taostats

  See [Staking Instructions](doc:staking-instructions) for a number of pages describing how to stake using Taostats.
</Callout>

<br />

Staking plays a principal role in the functioning of the Bittensor network. The principal goal of dTao is to divide chain emissions amongst subnets in a democratic way.  Staking into a subnet  increases the emissoins of the subnet.

# Staking Options

in dTao, there are two options for staking:

* [Staking to root](#staking-to-root)
* [Staking to a Subnet](#staking-to-alpha)

<br />

# Staking to root

Staking to root uses only tao.  Your tao is staked on a root validator, and you receive returns based on the validator's performance in the subnets.

Staking to root is a `safe`  staking option - there is no way to lose tao value.  However, root staking decreases over time [by design](doc:stakeholder-emissions-root-vs-alpha), as the root proportion decreases on all subnets.

<RootProp />

## Root Staking Options

If you have staked to root, by default your returns will be auto-compounded to your hotkey on root as tao.

Starting in fall 2025, you may also choose Root Claim (TODO)

<br />



This change over time is described in [Emissions: Root vs. Alpha Stake](doc:stakeholder-emissions-root-vs-alpha).

## Staking to alpha

This is the new feature and primary goal of dTao - to enable stakeholders to vote and determine the emissions for every subnet.

To stake in alpha, tao is exchanged via the [Subnet Pools](doc:subnet-pools) into alpha.  This will incur [Slippage](doc:slippage). The received alpha is then staked to the validator selected.  Your returns will be in alpha, and autocompounded to the validator hotkey.

Staking to alpha _does_ incur risk: a drop in alpha token price will result in a lower amout of tao when unstaking.

<br />

> 📘 Staking fees
>
> For all staking transactions, there is a small extrinsic fee charged.  Taostats currently does not allow staking without leaving a small amount of tao fee to pay for the unstaking transaction.
>
> ## Root
>
> There is no fee to stake or unstake from root
>
> ## Subnets:
>
> * All staking and unstaking fees are default 0.05% of the stake/unstake value.
> * Note that this can be changed by the subnet owner.
>
> ## Get the current fee for a subnet
>
> <StakingFee2 />

<br />

## Moving stake

The move stake command can be used to switch validators in a subnet.  Under the hood, this is an unstake, and then staking.  However, only one fee is charged.

<br />

## [dTao FAQ](doc:dtao-faq): Your top  staking questions

<br />

<br />
