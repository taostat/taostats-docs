---
title: What is Bittensor?
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: Bittensor Network Documentation & Analytics - Taostats Official Guide
  description: >-
    Explore the official Taostats documentation for the Bittensor network. Dive
    into detailed guides on subnets, miners, validators, and blockchain
    analytics. Your comprehensive resource for understanding and interacting
    with the decentralized Bittensor ecosystem, provided by Taostats.
  image: https://files.readme.io/27fdb8c-docs-meta-image.png
  keywords:
    - Bittensor
    - ' Taostats'
    - ' Blockchain Explorer'
    - ' Data Analytics'
    - ' Bittensor Documentation'
    - ' Bittensor Subnets'
    - ' Bittensor Miners'
    - ' Bittensor Validators'
    - ' Blockchain'
    - ' Decentralized Network'
    - ' Crypto'
    - ' Neurons'
    - ' Substrate'
    - ' Polkadot'
    - ' Delegation'
    - ' Consensus'
    - ' Cryptocurrency'
    - ' Network Stats'
    - ' Mining'
    - ' Staking'
  robots: index
next:
  description: ''
---
# Bittensor is a **Decentralised Incentivised Machine Learning Network and Digital Commodities Market**

Unpacking that statement:

- **Decentralised**: Unlike a centralised company where the infrastructure is controlled by a single entity, Bittensor is run on a distributed network of computers that are owned and operated by many (thousands) of different individuals or companies.  This decentralisation improves resilience, and removes central points of failure. 
- **Incentivised**: Incentivisation is achieved through the use of Bittensor's native token $TAO.  Participants are rewarded with tokens proportional to the value of their contribution to the network, with the lowest valued participants being replaced at a defined period  - ensuring that the entire network is not only performant but also strives to improve.
- **Machine Learning Network** Bittensor was designed around machine learning tasks. One of the biggest concerns in machine learning is compute power, and a decentralised machine learning network provides Bittensor participants with access to immense computing power. 
- **Digital Commodities Market** Although designed for machine learning, the (Re)evolution of Bittensor and the data agnostic principles of Yuma consensus have allowed it to adapt itself to not only provide a marketplace for Intelligence but for any digital commodity that can be produced and valued by network participants. 

# Bittensor Architecture

## [Subnets](doc:subnet)

The Bittensor chain is built on and supports multiple independently run sub-networks (subnets), with each subnet providing a [unique set of rules](doc:incentive-mechanisms) by which the participants produce the intelligence or digital commodity for which the subnet provides incentive.  These tasks are performed by [Miners](doc:mining) with the incentive value defined by a rewards landscape created by the coordinated contribution of [Validators](doc:validation), who are responsible for verifying and scoring the outputs of the miners.

> 📘 In May-July 2024, the Subnet count will grow from 32 to 64 subnets, at a rate of 4 new subnet slots a week.

## [Yuma Consensus](doc:consensus)

Each subnet has a different mechanism for scoring the work being created. The Yuma Consensus mechanism is used to aggregate scores from the subnets and determine how to distribute incentives and rewards across the participants of the network. It is agnostic to what is being measured and allows for fuzzy consensus around probabilistic truths such as intelligence which are also applicable to more binary forms of data.

## [Subtensor](doc:blockchain)

Subtensor is a substrate based blockchain which holds the incentivisation layer ensuring immutable records and  
distribution of a multiplicity of Bittensor incentive systems. All weights, consensus and network participation data are written to the chain along with transactions and account data.

## [Tao](doc:tao)

Tao is the native token of the Bittensor network. It is distributed to network participants (miners, validators, subnet owners and delegators) as it is emitted each block. 

# Bittensor Personas

There are several ways interested parties can participate in the Bittensor network:

- [User](doc:user)
- [Developer](doc:developer)
- [Miner](doc:miner)
- [Validator](doc:validator)
- [Staking](doc:staking)