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

Staking plays a principal role in the functioning of the Bittensor network. In February 2025, the dTao release gave stakeholders additional power: staking into a subnet increases the emissions of the subnet.

# Staking Options

in dTao, there are two options for staking:

* [Staking to root](#staking-to-root)
* [Staking to a Subnet](#staking-to-alpha)

<br />

# Staking to root

Staking to root uses only tao.  Your tao is staked on a root validator, and you receive returns based on the validator's performance in the subnets.

Staking to root is a `safe`  staking option - there is no way to lose tao value.  However, root staking decreases over time [by design](doc:stakeholder-emissions-root-vs-alpha), as the root proportion decreases on all subnets.

<RootProp />

Emission is rewarded ever 360 blocks (approximately 72 minutes)

<br />

## (Proposed) Root Staking Options 

In Fall 2025, the team has proposed the following change to the way root stake operates:

Emissions are not automatically awarded every 360 blocks, but will be awarded approximately daily.  The time will be random, and so may be sometimes longer than a day, sometimes less than a day.

Stakeholders will have two options in receiving rewards: 

### (Default) Root Claim

Root claim is the default option, and works similarly to the way root sketig works today. All the alpha earned will be converted to tao, and awarded to your root hotkey, approximately once a day.

### Alpha Claim

In fall 2025, root stakeholders may choose alpha claim.  This feature keeps your earned emission in alpha in every subnet.  IN this scenario, the claimed alpha is *not* converted to tao, but remains on the subnet staked as alpha.

<br />

<br />

# Staking to alpha

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
