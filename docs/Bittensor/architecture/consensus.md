---
title: Yuma Consensus
excerpt: The Yuma consensus mechanism
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
The Yuma Consensus algorithm translates weights into incentives for the subnet miners and dividends for the subnet validators. The Yuma Consensus rewards subnet validators with dividends for producing miner-value evaluations that are in agreement with the subjective evaluations produced by other subnet validators, weighted by stake.  The results of the subnet consensus are written to the blockchain to facilitate trustless rewards distribution.

Each subnet has its own incentive scoring incentive that awards miners for the value created in the subnet. Every <<glossary:epoch>> validators set their scored weights which are then processed by Yuma Consensus. Emission structure for each tao generated is based on this consensus.

# Subnet Emissions

1 tao is minted for each block that is created in the Bittensor blockchain (this occurs every 12 seconds). This emission is divided amongst the subnets based on weights set by validators in Subnet 0.

## Calculating Subnet Emissions

Subnet weights are defined in the [Root Subnet](doc:root-subnet) by validators using the cli command `btcli r weights`.  Validators can set a score for any or all subnets and their submitted scores are normalised to equal a total of 1.0 (100%). Here is an example screenshot from Taostats for the top 2 validators (based on stake):

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ab22b3a-image.png",
        null,
        "This chart can be found on the landing page: <https://taostats.io/>"
      ],
      "align": "center",
      "caption": "This chart can be found on the landing page: [taostats.io](https://taostats.io/)"
    }
  ]
}
[/block]


In this screenshot, the top validator ranks subnet 1 at 0.09 (9%), and validator 2 ranks subnet 1 at 0.04 (4%). The values allocated across the 32 subnets by each validator will always add up to 1.0 (100%). 

To calculate the total emissions Yuma Consensus takes into account both the score, the weight of the validator based on their stake and the consensus amongst the other validators weights to finalise the distribution of emissions across all subnets.  The distribution percentage for each subnet is shown across the header of the table.

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2Fm1QvCtfzHm0%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3Dm1QvCtfzHm0&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2Fm1QvCtfzHm0%2Fhqdefault.jpg&key=7788cb384c9f4d5dbbdbeffd9fe4b92f&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen; encrypted-media; picture-in-picture;\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=m1QvCtfzHm0",
  "title": "Bittensor Emissions deep-dive: Subnet emissions distribution",
  "favicon": "https://www.google.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/m1QvCtfzHm0/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=m1QvCtfzHm0",
  "typeOfEmbed": "youtube"
}
[/block]


<br>

## Subnet Emission Distribution

Each subnet's incentive mechanism breaks down the distribution of the Subnet's share of emissions to the active participants of the subnet.

- **Subnet Owner**: The subnet owner receives 18% of the emissions. 
- **Miner** Miners split 41% of emissions. 
- **Validator** Validators also split 41% of emissions. 

**Miners** are awarded emissions based on their emissions. Emissions are granted to each miner by validators, based on their incentive score derived from the quality of their work.  The evaluation criteria is set by the subnet incentive mechanism. See [Incentive for Miners](doc:consensus-for-miners) for more detail on how incentive is awarded to miners.

**Validators** are awarded emissions based on the amount of tao they have staked, and the performance and consensus with other validators on the network, represented by the vtrust metric. See [Incentive for Validators](doc:incentive-for-validators) for more detail on how incentive is awarded to validators.

<br>