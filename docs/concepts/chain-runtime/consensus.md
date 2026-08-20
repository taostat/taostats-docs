---
title: Neuron Rewards Mechanism
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

The Yuma consensus mechanism

The Yuma Consensus algorithm translates weights into emissions.

Validators test the output of miners, and grade the results as weights.  These weights are passed to Yuma Consensus.  The Yuma Consensus algorithm translates weights into incentives for the subnet miners and dividends for the subnet validators. The Yuma Consensus rewards subnet validators with dividends for producing miner-value evaluations that are in agreement with the subjective evaluations produced by other subnet validators, weighted by stake.  The results of the subnet consensus are written to the blockchain to facilitate trustless rewards distribution.

# Checks and Balances

While setting the emissions for participants of the network, the algorithm also checks for Consensus. If the weights placed by a validator are not "in consensus" or similar to the other scores submitted by other validators, the results are given less "weight."

This works as a check against bad actor validators who might try to manipulate the system for their own gain.

## TL;dr:

If all the validators agree that a miner is doing a good job - they get a higher reward (incentive).
The more that the validators agree on miner performance - the higher their rewards.

## Examples

* **Miner** Validator `SuperTao` has 10 miners running in Subnet 85.  The validator gives these miners extremely high scores, and very low scores to the remaining miners - a drastic difference from the other validators.  The weights placed by `SuperTao` will be largely ignored by the Yuma Consensus engine.  Also, the VTrust score for `SuperTao` will be lowered — directly affecting the Dividends and emission awarded to the Validator.

<Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=FT0gL4MXgMM" href="https://www.youtube.com/watch?v=FT0gL4MXgMM" providerUrl="https://www.youtube.com/" providerName="YouTube" />
