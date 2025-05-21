---
title: Validator (Architecture)
excerpt: >-
  Validators are the neurons in a subnet that validate miner output and provide
  gateway access to the network
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
> 📘 This section focuses on the validator architecture inside a subnet.
> 
> The [Validator Persona](doc:validator) has details on how a validator can be run.

On each subnet there are a configurable number slots reserved for validation (default: 64). IN practice, these slots are not all filled by validators, and miners can use these slots as well.

Validators have three primary roles. Two exist inside  each subnet, and the third is to rank each subnet.

1. **Validation of miner output**.  This is usually done by sending regular requests to each miner and then assigning a value/score to the response.  These scores are usually added to a moving average of the miners performance which enables a score (weights) to be set at regular intervals on the blockchain for all miners by that validator. These weights form part of the incentive landscape which when combined with the weights of the other validators using [Yuma Consensus](doc:consensus) are then used to define and distribute emissions.
2. **Gateway access to the network**. The only way a user or application can query a subnet is through the hotkey of an active validator - therefore validators also act as trusted gateways to the miners which in turn allows miners to prioritise queries based on a stake.
3. **Subnet Emissions** Emissions to the subnet are no longer determined by validator weighs on the root Subnet.  But - stake is still routhed through validators on each subnet.  See [Emissions for Validators](doc:incentive-for-validators), [Emissions: Root vs. Alpha Stake](doc:stakeholder-emissions-root-vs-alpha) for further details.

The amount of tao a validator has as delegated stake defines both the value of the weights they set for miners and as a result allows for a natural market prioritisation of access to form.

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FMLVeSRZoU7g%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DMLVeSRZoU7g&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FMLVeSRZoU7g%2Fhqdefault.jpg&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen; encrypted-media; picture-in-picture;\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=MLVeSRZoU7g",
  "title": "Bittensor Overview: Validators",
  "favicon": "https://www.youtube.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/MLVeSRZoU7g/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=MLVeSRZoU7g",
  "typeOfEmbed": "youtube"
}
[/block]


<br />

# Validation

Validators must assess how well the miners are performing and the value they create on the network.  Each subnet has a different [Incentive Mechanism](doc:incentive-mechanisms) for determining how the validator interacts with the miner and scores the responses.

This is done by creating synthetic queries or tasks that are sent to the miners to respond to or perform. This is done in a way that the validator either knows the correct or best response the miner can give, or is able to score the response when compared to the responses of the other miners. 

The incentive mechanism is not fixed and it is the possibility for design of unique and innovative incentive mechanisms that is one of the key values of the network allowing each subnet a different approach to validation.

## Parent/Child hotkeys

Validators can share stake with other validators by becoming a parent hotkey. This allows the parent to share a percentage of stake (from 0-100%) with the child hotkey.  See [Child Hotkeys](doc:child-hotkeys) for more details.

## Weight copying

[Weight Copying](doc:weight-copying) occurs when a validator does not perform actual miner validation, but copies the weights of other validators.  The Bittensor team has added encrypted weights in an attempt to mitigate this issue.

## Minimum Stake

Some subnets have a minimum stake required to be a successful validator. Below this minimum value, weights set by a validator would have near zero effect on the miner's emissions.

<br />

## Validator Registration

Learn how to [register a node](doc:node-registration) on a subnet.

In addition to the steps in the above link, validators need to have a significant amount of TAO staked to their hotkey to be successful in validating miners. This is due to market dynamics incentivising miners to naturally prioritise requests from validators with more stake as their weights hold great influence over consensus of trust. 

Although this varies from subnet to subnet there is a hard floor of 1k tao with a generally accepted competitive functional floor of around 20k tao (at the time of writing). This means that whilst is is possible to validate with less than 20k tao, you may not achieve the same level of responses from all miners and as a result consensus in the weights you set, and as a result your appropriate share of emissions. 

It should also be noted that in order to validate competitively you must be present on as many subnets as possible.  This increases your emissions, and thus the return to the stakeholders.

There is a real world cost to running this infrastructure which also makes it not profitable below a certain threshold of staked tao. 

> 📘 How can miners ignore validators?
> 
> If a validator has a very low amount of tao staked, their scoring has very little weight in Consensus.   Ignoring a validator allows the miner to focus on the validators that will impact their score (and create the subnet's output).

## Validator Emission

Validators are awarded emission from the network based on their dividend score.  Dividend is evaluated from the stake and Vtrust values. Vtrust describes how well their weights match the **consensus** of other validators.  See [Emissions for Validators](doc:incentive-for-validators))  for a detailed analysis.

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=http%3A%2F%2Fwww.youtube.com%2Fembed%2Fvideoseries%3Flist%3DPLYW5tJU0VYmgMoMuDcjL9lfc6tVE3zzLd&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fplaylist%3Flist%3DPLYW5tJU0VYmgMoMuDcjL9lfc6tVE3zzLd&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FXUgoBN8VB7Q%2Fhqdefault.jpg%3Fsqp%3D-oaymwEXCOADEI4CSFryq4qpAwkIARUAAIhCGAE%3D%26rs%3DAOn4CLDnKExP-CILW4skZCS2JCVslwQHAA%26days_since_epoch%3D19969&key=02466f963b9b4bb8845a05b53d3235d7&type=text%2Fhtml&schema=youtube\" width=\"853\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen; encrypted-media; picture-in-picture;\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/playlist?list=PLYW5tJU0VYmgMoMuDcjL9lfc6tVE3zzLd",
  "title": "Bittensor Validation",
  "favicon": "https://www.youtube.com/s/desktop/4151fd0f/img/favicon.ico",
  "image": "https://i.ytimg.com/vi/XUgoBN8VB7Q/hqdefault.jpg?sqp=-oaymwEXCOADEI4CSFryq4qpAwkIARUAAIhCGAE=&rs=AOn4CLDnKExP-CILW4skZCS2JCVslwQHAA&days_since_epoch=19969",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/playlist?list=PLYW5tJU0VYmgMoMuDcjL9lfc6tVE3zzLd",
  "typeOfEmbed": "youtube"
}
[/block]


# Gateway Access

As miners are only scored by validators there is no incentive for them to receive or trust requests from anyone else except a valid validator.  Any request to the miners must therefore pass through a validator which will be routed to a miner(s)  who will generate the response to the validator, who returns the response to the external user.

This allows validators to build API infrastructure or allow their access to be valued by any other network participant providing API access to the network.

An example of this is [Corcel](https://corcel.io) who provide API access to a number of subnets via their validator,  and on subnets running the code they are able to purchase bandwidth from multiple validators therefore 'load-balancing' the queries across multiple validators access promoting a healthy decentralisation of network traffic.

This is just one way of facilitating access to the network data via a validator and constant advancements a birthing new and innovative ways to interface with the commodities produced by subnets.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1492508-image.png",
        null,
        ""
      ],
      "align": "center",
      "sizing": "75% "
    }
  ]
}
[/block]