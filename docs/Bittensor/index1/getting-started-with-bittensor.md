---
title: Getting Started with Bittensor
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  image: https://files.readme.io/0656024-taostatsicon.png
  robots: index
next:
  description: ''
---
# Getting Started with Bittensor

There are several ways to get started with Bittensor, with different levels of participation. We will list these personas based on the requirements for entry into the Bittensor ecosystem.

## Users: No Barrier to Entry

- **[User](doc:user)**: Applications that are built on top of Bittensor will have users that interact with them. These applications will make API calls into the Bittensor network, and the user is not required to know that the application is powered by Bittensor or have knowledge of the eco-system.  These applications can be free or paid as the developers dictate, but there is no requirement that the revenue stream utilises the tao token (payments could be by credit card in FIAT or any other digital currency).  You can try several free applications built on Bittensor at [corcel](https://app.corcel.io).

## Developers: API Token

- **[Developer](doc:developer)**:  Developers build applications that utilise the commodities being produced by the Bittensor network.  Whilst validators provide gateway access to the network, developers who are not aligned with a validator must use an API key to query the network through a participating validator. Obtaining and interacting with the data can vary from subnet to subnet, however products such as [Corcel](https://docs.corcel.io) exist to make interaction with many subnets easy via a single API key.

  Currently API access to the network is supported through incentivisation. This provides a highly cost competitive  space for developers and actively encourages network growth - however it is likely in the future that access at scale for profit will incur charges.

## Token: Participants

- **[Delegators](doc:delegation)**: Delegation of stake (often referred to as staking) is the process of attaching your tao to a validator.  When you stake with a validator, you receive a percentage of the rewards earned by the validator. It is possible to delegate any amount of tao to a validator so whilst you must hold the token, the associated cost is defined by the individual.
- **[Validators](doc:validator)**: Validators handle all incoming requests to a subnet and also perform validation on the work performed by the miners.  Validators are rewarded with a percentage of the tao emitted each epoch. In order to be a validator you must possess or have delegated a sufficient amount of tao to attain [vpermit](<>) on any subnet you wish to validate. Whilst this varies between subnets, this figure is currently in the range of 5-20k tao so is the largest barrier to entry of the participants. 
- **[Miners](doc:miner)**:  Actors that complete the requests on the subnet.  Miners are rewarded based on the value of their outputs via their trust score governed by the validation process. A miner requires tao to register a UID on a given subnet. There is a tao cost/recycle to this which is proportional to the demand for slots on that subnet and varies greatly from subnet to subnet. This makes mining the lowest participant barrier to entry.
- **[Subnet Owners](subnets)**: The individual or organisation that creates a subnet.  They devise the model for the subnet, and the incentive mechanism, and develop the code for both miners and validators. Subnet owners are required to lockup tao in order to register a subnet. The cost is dynamic and governed by current demand for subnet slots. This provides a significant barrier to entry but the rewards for successful subnet operation are considerable and the fee is locked and not burned.