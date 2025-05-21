---
title: Weight Copying
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
Weight copying is a controversial topic in the Bittensor community.  In this article, we look to *explain* weight copying and pros and cons of weight copying.

# What is weight copying?

Validators weigh the work of each miner and create a ranked scoring - this is called setting weights.  The weights are taken to the Yuma consensus to create the trust score for all of the validators.

Vtrust is the scoring of validators - and to score well in Vtrust, your weights must be similar to those of every other validator.

**weight copying** is when a validator copies the scores from the Yuma consensus, and uses them to place their weights.  This ensures a high Vtrust.

# Why Weight copying?

When a validator uses the scoring from the Yuma consensus to place weights - they will score an extremely high Vtrust.  High Vtrust leads to a higher percentage of emissions - which leads to higher revenue.

* On some subnets, miners will actively ignore requests from validators with low stake.  To get a high stake, you need good results.  It puts new validators in a chicken/egg situation.  By weight copying, the validator is able to show good returns, and gain delegation.  

## Reasons to not weight copy

Validators that weight copy are not contributing to the Bittensor ecosystem.  Validation of the miners is an essential part of the checks and balances of the Biottensor ecosystem.  Weight copying does not give back into the ecosystem, and pushes the work onto a smaller group of validators.

Subnets are beginning to block access to the data to validators who weight copy - forcing all nodes to be active participants in the network.

# Weight copying in Taostats

Validators who are suspected of weight copying have their `nom/24 HR/1ktao`score in red.  This indicates that while their return may be higher, that they are not contributing back to the bittensor community.  If you are staking tao, you can choose to support the community and those validators who are giving back.

# Responses to Weight copying: Commit Reveal

In Bittensor 7.3.0, Commit Reveal was launched. Weights submitted to the root network are encrypted for a certain number of blocks.  This feature, know as commit reveal can be used to hide the current weights that each validator places on the root subnet.  The code was released so that subnet owners could do the same in their subnets: validator weights would be encrypted for a known number of blocks, preventing weight copiers from using fresh data, and making it hard for them to be successful as weight copying validators. The Bittensor team have released a [blog post](https://blog.bittensor.com/weight-copying-in-bittensor-422585ab8fa5)  and [technical whitepaper](https://docs.bittensor.com/papers/BT-Consensus-based-Weights.pdf)  on their research on commit reveal and its effect of weight copying.
