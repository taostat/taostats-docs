---
title: Getting Started with Bittensor
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

There are several ways to get started with Bittensor, with different levels of participation. We will list these personas based on the requirements for entry into the Bittensor ecosystem.

## Users: No Barrier to Entry

* **[User](/docs/user)**: Applications that are built on top of Bittensor will have users that interact with them. These applications will make API calls into the Bittensor network, and the user is not required to know that the application is powered by Bittensor or have knowledge of the eco-system.  These applications can be free or paid as the developers dictate, but there is no requirement that the revenue stream utilises the tao token (payments could be by credit card in FIAT or any other digital currency).

## Developers: API Token

* **[Developer](/docs/developer)**:  Developers build applications that utilise the commodities being produced by the Bittensor network.  Whilst validators provide gateway access to the network, developers who are not aligned with a validator must use an API key to query the network through a participating validator. Obtaining and interacting with the data can vary from subnet to subnet, however products such as [nineteen.ai](https://nineteen.ai/) exist to make interaction with many subnets easy via a single API key.

  Currently API access to the network is supported through incentivisation. This provides a highly cost competitive  space for developers and actively encourages network growth - however it is likely in the future that access at scale for profit will incur charges.

## Token: Participants

* **[Delegators](/docs/delegation)**: Delegation of stake (often referred to as staking) is the process of staking your alpha (or tao converted into alpha) to a validator's hotkey on a subnet. When you stake, rewards are paid in that subnet's alpha and credited to the hotkey you staked to. It is possible to stake any amount to a validator so whilst you must hold the token, the associated cost is defined by the individual.
  * [Staking/Delegation](/docs/staking)
  * [Staking Instructions](/docs/staking-instructions)
* **[Validators](/docs/validator)**: Validators handle all incoming requests to a subnet and also perform validation on the work performed by the miners.  Validators are rewarded with a percentage of the subnet alpha emitted each epoch. In order to be a validator you must possess or have delegated a sufficient amount of tao to successfully validate. Whilst this varies between subnets, this figure is currently in the range of 5-20k tao so is the largest barrier to entry of the participants.
  * [Running a Validator](/docs/validator)
* **[Miners](/docs/miner)**:  Actors that complete the requests on the subnet.  Miners are rewarded subnet alpha token based on the value of their outputs via their trust score governed by the validation process. A miner requires tao to register a UID on a given subnet. There is a tao cost/recycle to this which is proportional to the demand for slots on that subnet and varies greatly from subnet to subnet. This makes mining the lowest participant barrier to entry.
  * [Taostats: For Miners](/docs/taostats-for-miners)
  * [Starting as a Miner](/docs/i-want-to-mine-on-bittensor)
* **[Subnet Owners](subnets)**: The individual or organisation that creates a subnet.  They devise the model for the subnet, and the incentive mechanism, and develop the code for both miners and validators. Subnet owners are required to lockup tao in order to register a subnet. The cost is dynamic and governed by current demand for subnet slots. This provides a significant barrier to entry but the rewards for successful subnet operation are considerable. A portion of the fee is paid into the subnet's liquidity pool and the remainder is recycled.
  * [Subnet Owner](/docs/subnet-owner)
  * [Subnet Owner Startup Guide](/docs/subnet-owner-startup-guide)
