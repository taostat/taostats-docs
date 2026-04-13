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
The Yuma Consensus algorithm translates weights into emissions. 

# Neuron Rewards Mechanism

Validators test the output of miners, and grade the results as weights.  These weights are passed to Yuma Consensus.  The Yuma Consensus algorithm translates weights into incentives for the subnet miners and dividends for the subnet validators. The Yuma Consensus rewards subnet validators with dividends for producing miner-value evaluations that are in agreement with the subjective evaluations produced by other subnet validators, weighted by stake.  The results of the subnet consensus are written to the blockchain to facilitate trustless rewards distribution.


# Checks and Balances

While setting the emissions for participants of the network, the algorithm also checks for Consensus. If the weights placed by a validator are not "in consensus" or similar to the other scores submitted by other validators, the results are given less "weight."  

This works as a check against bad actor validators who might try to manipulate the system for their own gain.

## TL;dr:
If all the validators agree that a miner is doing a good job - they get a higher reward (incentive).
The more that the validators agree on miner performance - the higher their rewards.


## Examples

* **Miner** Validator `SuperTao` has 10 miners running in Subnet 85.  The validator gives these miners extremely high scores, and very low scores to the remaining miners - a drastic difference from the other validators.  The weights placed by `SuperTao` will be largely ignored by the Yuma Consensus engine.  Also, the VTrust score for `SuperTao` will be lowered - directly effecting the Dividends and emission awarded to the Validator.

<Embed url="https://www.youtube.com/watch?v=FT0gL4MXgMM" title="Bittensor TAO - Yuma Consensus and VTrust" favicon="https://www.youtube.com/favicon.ico" image="https://i.ytimg.com/vi/FT0gL4MXgMM/hqdefault.jpg" provider="youtube.com" href="https://www.youtube.com/watch?v=FT0gL4MXgMM" typeOfEmbed="youtube" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252FFT0gL4MXgMM%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253DFT0gL4MXgMM%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252FFT0gL4MXgMM%252Fhqdefault.jpg%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" />
