---
title: Getting Started with Bittensor
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  image: >-
    https://files.readme.io/6589c5f085ff82cfcae99f551d7bfe7d9085a0824671efe020080a7a31417252-04a0e649e8e099c53848ad52fab8e766cb5a967074721b6c94d0128a7130680d-5c7ec0ef615eab848d8b67f51dc7420704504a7c21a179b3ce401ee84528e5bc-taostats-docs_waifu2x_scale4x.png
  robots: index
next:
  description: ''
---
# Getting Started with Bittensor

There are several ways to get started with Bittensor, with different levels of participation. We will list these personas based on the requirements for entry into the Bittensor ecosystem.

## Users: No Barrier to Entry

* **[User](doc:user)**: Applications that are built on top of Bittensor will have users that interact with them. These applications will make API calls into the Bittensor network, and the user is not required to know that the application is powered by Bittensor or have knowledge of the eco-system.  These applications can be free or paid as the developers dictate, but there is no requirement that the revenue stream utilises the tao token (payments could be by credit card in FIAT or any other digital currency).

## Developers: API Token

* **[Developer](doc:developer)**:  Developers build applications that utilise the commodities being produced by the Bittensor network.  Whilst validators provide gateway access to the network, developers who are not aligned with a validator must use an API key to query the network through a participating validator. Obtaining and interacting with the data can vary from subnet to subnet, however products such as [Corcel](https://docs.corcel.io) exist to make interaction with many subnets easy via a single API key.

  Currently API access to the network is supported through incentivisation. This provides a highly cost competitive  space for developers and actively encourages network growth - however it is likely in the future that access at scale for profit will incur charges.

## Token: Participants

* **[Delegators](doc:delegation)**: Delegation of stake (often referred to as staking) is the process of attaching your tao to a validator on.a subnet.  When you stake with a validator, you receive a percentage of the rewards earned by the validator. It is possible to delegate any amount of tao/alpha to a validator so whilst you must hold the token, the associated cost is defined by the individual.
  * [Staking/Delegation](doc:staking)
  * [Staking Instructions](doc:staking-instructions)
* **[Validators](doc:validator)**: Validators handle all incoming requests to a subnet and also perform validation on the work performed by the miners.  Validators are rewarded with a percentage of the subnet alpha emitted each epoch. In order to be a validator you must possess or have delegated a sufficient amount of tao to successfully validate. Whilst this varies between subnets, this figure is currently in the range of 5-20k tao so is the largest barrier to entry of the participants.
  * [Running a Validator](doc:validator)
* **[Miners](doc:miner)**:  Actors that complete the requests on the subnet.  Miners are rewarded subnet alpha token based on the value of their outputs via their trust score governed by the validation process. A miner requires tao to register a UID on a given subnet. There is a tao cost/recycle to this which is proportional to the demand for slots on that subnet and varies greatly from subnet to subnet. This makes mining the lowest participant barrier to entry.
  * [Taostats: For Miners](doc:taostats-for-miners)
  * [Starting as a Miner](doc:i-want-to-mine-on-bittensor)
* **[Subnet Owners](subnets)**: The individual or organisation that creates a subnet.  They devise the model for the subnet, and the incentive mechanism, and develop the code for both miners and validators. Subnet owners are required to lockup tao in order to register a subnet. The cost is dynamic and governed by current demand for subnet slots. This provides a significant barrier to entry but the rewards for successful subnet operation are considerable and the fee is locked and not burned.
  * [Subnet Owner](doc:subnet-owner)
  * [Subnet Creation Best Practices](doc:subnet-creation-best-practices)
