---
title: Staking/Delegation
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
A tao token holder can earn a share of emissions by delegating stake to one or multiple validators.

The more tao delegated to a validator, the greater proportion of network access they are granted and the greater their weight in all aspects of Yuma consensus calculations.  

The validator's emissions are shared proportional to stake amongst all of those who have staked tao. Validators can take a commission from the staking emissions.  This is defined through the `take` parameter, and can range from 0-18% with 18% as the default value.

## Calculate your Staking rewards

If your validator has emission of x tao, you can find your staking rewards as follows:

![](https://files.readme.io/55bad92-image.png)

taostats reports emission per epoch (360 blocks).  multiple by 20 to get an estimate of daily reward.

## nom/1k/24hours

Taostats calculates the nom/1ktao/24hours - or how much a nominator would receive in 24 hours if they have 1,000 tao staked to the validator.  Multiply \*1000 and divide by your stake to get your daily return.

# Why Stake?

Staking is a way for a holder of TAO to earn emissions without running a subnet/validator/miner and as a result retain value of the token whilst the supply increases due to continued token issuance. By staking with a validator, they are giving *weight* and showing support to that validator's actions on the network. 

## Is staking safe?

Yes. your tao remains associated with your coldkey.  It is never in the validator's wallet.

## Staking limits

One stake/unstake event per wallet and validator every 360 blocks.  So if you make a test stake - you have to wait 360 block (about 72 minutes) to do the full stake.  Or if you want to immediately unstake - you must wait 72 minutes.

# Staking TAO

Stake TAO with:

* [Command Line Tool](doc:command-line-tool)
* <a href=" https://delegate.taostats.io" target="_blank">Taostats</a>

# Helpful links

* [Taostats: For Staking](doc:taostats-for-staking): The Bittensor data you need to make staking decisions.
* [Staking FAQ](https://docs.taostats.io/docs/faq#stakingdelegation)
