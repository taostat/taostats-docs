---
title: What is Bittensor?
excerpt: >-
  The Taostats docs are a great introduction to Bittensor and ghow to explore
  Bittensor with Taostats.
deprecated: false
hidden: false
metadata:
  title: Bittensor Network Documentation & Analytics - Taostats Official Guide
  description: >-
    Explore the official Taostats documentation for the Bittensor network. Dive
    into detailed guides on subnets, miners, validators, and blockchain
    analytics. Your comprehensive resource for understanding and interacting
    with the decentralized Bittensor ecosystem, provided by Taostats.
  image: >-
    https://files.readme.io/48d52d923046397bb25d995e84af15dad105e9a552695756d04795fdda5b261d-04a0e649e8e099c53848ad52fab8e766cb5a967074721b6c94d0128a7130680d-5c7ec0ef615eab848d8b67f51dc7420704504a7c21a179b3ce401ee84528e5bc-taostats-docs_waifu2x_scale4x.png
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

* **Decentralised**: Unlike a centralised company where the infrastructure is controlled by a single entity, Bittensor is run on a distributed network of computers that are owned and operated by many (thousands) of different individuals or companies.  This decentralisation improves resilience, and removes central points of failure. 
* **Incentivised**: Incentivisation is achieved through the use of Bittensor's native token $TAO.  Participants are rewarded with tokens proportional to the value of their contribution to the network, with the lowest valued participants being replaced at a defined period  - ensuring that the entire network is not only performant but also strives to improve.
* **Machine Learning Network** Bittensor was designed around machine learning tasks. One of the biggest concerns in machine learning is compute power, and a decentralised machine learning network provides Bittensor participants with access to immense computing power. 
* **Digital Commodities Market** Although designed for machine learning, the (Re)evolution of Bittensor and the data agnostic principles of Yuma consensus have allowed it to adapt itself to not only provide a marketplace for Intelligence but for any digital commodity that can be produced and valued by network participants. 

# Bittensor Architecture

<br />

<Embed url="https://www.youtube.com/watch?v=aoAiV4frT-M" title="How does Bittensor work?" favicon="https://www.youtube.com/favicon.ico" image="https://i.ytimg.com/vi/aoAiV4frT-M/hqdefault.jpg" provider="youtube.com" href="https://www.youtube.com/watch?v=aoAiV4frT-M" typeOfEmbed="youtube" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252FaoAiV4frT-M%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253DaoAiV4frT-M%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252FaoAiV4frT-M%252Fhqdefault.jpg%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" />

## [Subnets](doc:subnet)

The Bittensor chain is built on and supports multiple independently run sub-networks (subnets).  

* Each subnet provides a [unique set of tasks and rules](doc:incentive-mechanisms) by which the participants produce the intelligence or digital commodity for which the subnet provides incentive.  
* Tasks are performed by [Miners](doc:mining) with the incentive value defined by a rewards landscape created by the coordinated contribution of [Validators](doc:validation), who are responsible for verifying and scoring the outputs of the miners.

## [Yuma Consensus](doc:consensus)

Each subnet has a different mechanism for scoring the work being created. The Yuma Consensus mechanism is used to aggregate scores from the subnets and determine how to distribute incentives and rewards across the participants of the network. It is agnostic to what is being measured and allows for fuzzy consensus around probabilistic truths such as intelligence which are also applicable to more binary forms of data.

## [Subtensor](doc:blockchain)

Subtensor is a substrate based blockchain which holds the incentivisation layer ensuring immutable records and distribution of a multiplicity of Bittensor incentive systems. All weights, consensus and network participation data are written to the chain along with transactions and account data.

## [Tao](doc:tao)

Tao is the native token of the Bittensor network. It is distributed to the Subnet pools as it is emitted each block. 

## [Alpha](doc:alpha-tokens)

Each Subnet has a token that is used to incentivise participants of the subnet. The generic term for these subnet tokens is alpha (which is also the name of the token on Subnet 1.  Each subnet's token has a name (taken from Green, Hebrew, Arabic, etc. ) alphabets in order to disambiguate from other subnet tokens.  However, to simplify discussions all subnet tokens can gbe generalised as alpha.

Alpha can only be exchanged with tao, via subnet pools.

# Bittensor Personas

There are several ways interested parties can participate in the Bittensor network:

* [User](doc:user)
* [Developer](doc:developer)
* [Miner](doc:miner)
* [Validator](doc:validator)
* [Subnet Owner](doc:subnet-owner)
* [Staking](doc:staking)