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

- **Decentralised**: Unlike a centralised company where the infrastructure is controlled by a single entity, Bittensor is run on a distributed network of computers that are owned and operated by many (thousands) of different individuals or companies.  This decentralisation improves resilience, and removes central points of failure. 
- **Incentivised**: Incentivisation is achieved through the use of Bittensor's native token $TAO.  Participants are rewarded with tokens proportional to the value of their contribution to the network, with the lowest valued participants being replaced at a defined period  - ensuring that the entire network is not only performant but also strives to improve.
- **Machine Learning Network** Bittensor was designed around machine learning tasks. One of the biggest concerns in machine learning is compute power, and a decentralised machine learning network provides Bittensor participants with access to immense computing power. 
- **Digital Commodities Market** Although designed for machine learning, the (Re)evolution of Bittensor and the data agnostic principles of Yuma consensus have allowed it to adapt itself to not only provide a marketplace for Intelligence but for any digital commodity that can be produced and valued by network participants. 

# Bittensor Architecture

<br />

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FaoAiV4frT-M%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DaoAiV4frT-M&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FaoAiV4frT-M%2Fhqdefault.jpg&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen; encrypted-media; picture-in-picture;\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=aoAiV4frT-M",
  "title": "How does Bittensor work?",
  "favicon": "https://www.youtube.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/aoAiV4frT-M/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=aoAiV4frT-M",
  "typeOfEmbed": "youtube"
}
[/block]


## [Subnets](doc:subnet)

The Bittensor chain is built on and supports multiple independently run sub-networks (subnets).  

- Each subnet provides a [unique set of tasks and rules](doc:incentive-mechanisms) by which the participants produce the intelligence or digital commodity for which the subnet provides incentive.  
- Tasks are performed by [Miners](doc:mining) with the incentive value defined by a rewards landscape created by the coordinated contribution of [Validators](doc:validation), who are responsible for verifying and scoring the outputs of the miners.

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

- [User](doc:user)
- [Developer](doc:developer)
- [Miner](doc:miner)
- [Validator](doc:validator)
- [Subnet Owner](doc:subnet-owner)
- [Staking](doc:staking)