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
The Yuma Consensus algorithm translates weights into emissions. There are two places that Yuma is used in the Bittensor Network.

# Subnet Emissions

Validators in the [Root Subnet](doc:root-subnet) place weights for each Subnet in the form of a percentage. Yuma consensus weighs these by the amount of stake each validator has, and generates the emission percentage for each Subnet.

# Neuron Rewards Mechanism

Validators test the output of miners, and grade the results as weights.  These weights are passed to Yuma Consensus.  The Yuma Consensus algorithm translates weights into incentives for the subnet miners and dividends for the subnet validators. The Yuma Consensus rewards subnet validators with dividends for producing miner-value evaluations that are in agreement with the subjective evaluations produced by other subnet validators, weighted by stake.  The results of the subnet consensus are written to the blockchain to facilitate trustless rewards distribution.

# Checks and Balances

While setting the emissions for participants of the network, the algorithm also checks for Consensus. If the weights placed by a validator are not "in consensus" or similar to the other scores submitted by other validators, the results are given less "weight."  

This works as a check against bad actor validators who might try to manipulate the system for their own gain.

## Examples

- **Root Subnet**: Validator `SuperTao` also runs Subnet 70.  They decide that the correct emission strategy for the entire Bittensor network is to give subnet 70 100% of their emissions, and 0% to every other subnet.  All of the other validators divide their emission amongst the many Subnets providing value.  This validator is out of consensus with the other validators, and as a result, their Subnet Emission profile will be largely ignored.
  - Note that the difference does not have to be this drastic.  Even emission scores 10% higher than other validators will be seen as out of consensus.
- **Miner** Validator `SuperTao` has 10 miners running in Subnet 85.  The validator gives these miners extremely high scores, and very low scores to the remaining miners - a drastic difference from the other validators.  The weights placed by `SuperTao` will be largely ignored by the Yuma Consensus engine.  Also, the VTrust score for `SuperTao` will be lowered - directly effecting the Dividends and emission awarded to the Validator.

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FFT0gL4MXgMM%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DFT0gL4MXgMM&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FFT0gL4MXgMM%2Fhqdefault.jpg&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen; encrypted-media; picture-in-picture;\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=FT0gL4MXgMM",
  "title": "Bittensor TAO - Yuma Consensus and VTrust",
  "favicon": "https://www.youtube.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/FT0gL4MXgMM/hqdefault.jpg",
  "provider": "https://www.youtube.com/",
  "href": "https://www.youtube.com/watch?v=FT0gL4MXgMM",
  "typeOfEmbed": "youtube"
}
[/block]