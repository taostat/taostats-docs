---
title: Running a Validator
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
A validator operates validator nodes on subnets of the Bittensor network. The person (or organisation) behind the validator is afforded gateway access to the intelligence and commodities produced by the subnets on which they operate allowing them the ability to build infrastructure and facilitate external access to the network.

Validators are tasked with both measuring and rewarding the value produced by the network from within the code structure of each subnet, but also through external activities unique to each validator which are aimed to win approval and trust of the community which will be rewarded with delegated stake, affording greater network access.

A validators performance in a subnet is measured through their consensus with the other validators, measured by the vtrust metric, attained through the process of scoring and setting weights to the miners.  Validators whose scores are in agreement/consensus with the rest of the validators have a higher vtrust and as a result earn more performant rewards..

> 📘 TL;dr of successful validation
> 
> 1. The more stake your validator has - the higher the dividends/emission in each subnet.  
>    1. Many subnets have minimum stake requirements (as high as 25k tao).
> 2. For the highest stakeholder return, you must validate on as many subnets as possible - returns are additive across subnets.
>    1. Take & child take can be manipulated in each subnet to maximize returns.

# Subnet Validation

Each subnet uses a unique validation and rewards mechanism to define the value of the commodity being produced and assign incentive rewards for this process. Miners complete tasks based on the subnet mechanism requirements and the validators verify, compare and score the responses.  The scores are collated, normalised and submitted as weights for consensus, published to the blockchain.

The output of the consensus (rewards landscape) is the breakdown of the rewards for the validators, miners, and subnet owners. These results are recorded on the blockchain.

To see a validator's results in Taostats, x.taostats.io/validator/<hotkey> has a wealth of detail:

- For each subnet that the validator is active:

![](https://files.readme.io/98aaa2e-image.png)

See [Taostats: For Validators](doc:taostats-for-validators) for more details

# Stake/delegation

Validators are incentivised to add value to the Bittensor ecosystem.  This value is recognised and rewarded by participants delegating [Stake](doc:staking) to their validator(s) of choice.  The more stake a validator has, the  greater proportion of network bandwidth is afforded to them through the natural market effect of their weights holding higher value to miners as a result of the prioritisation of stake by Yuma Consensus. (Higher stake also maximises emissions for the validator.)

This can also be enforced through subnet mechanisms such as Subnet 19 - Vision which enables inference at scale whilst allocating bandwidth based upon the proportion of total delegation held.

![](https://files.readme.io/1f945c1-image.png)

To reward those that stake on a validator, the validator's emissions are divided amongst all delegators.

# Emissions

Validators on each subnet receive 41% of all emissions. This is divided amongst the validators based upon their current performance on a given subnet.  The dividend metric is the fraction of validator emission for each validator. It is determined from the vtrust metric, proportional to the total stake they hold on any given subnet. Validators with high VTrust and high stake will maximise returns.

## Child Take

If the validator has an active neuron, they can set a child take - if another validator places a parent hotkey on the validator's neuron, the child hotkey is awarded a percentage of their award.

## Take

As emission is divided to delegators, the validator can take a small percentage of the emissions. This is called the `take`. Today, validators can set this percentage (using the [Command Line Interface (CLI)](doc:command-line-tool)) to be any value from 0-18% (the default value is 18%).

See the [Tao Allocation](doc:tao-allocation) for a model of the percentages a validator can earn. 

The remainder of the emission is distributed the the stakeholders.

# Subnet weighting (Root subnet)

Validators can set emissions weights for every subnet (assuming they are registered on the [Root Subnet](doc:root-subnet)), which also uses [Yuma Consensus](doc:consensus) to then determine the emissions for each subnet.

# Senate

Validators may also elect to join the [Senate](doc:senate) provided they are present on the Root Subnet and are in the top 8 validators (by stake) who have elected to be senate members.

# List of Validators and Verification

In order to be recognised as a validator the participant much and on-chain verification of the ownership of their key using the [Bittensor Delegates](https://github.com/opentensor/bittensor-delegates/) repository. The full list of all keys and the associated metadata they submitted can be see on a [public delegates.json file](https://github.com/opentensor/bittensor-delegates/blob/main/public/delegates.json) which is used for labelling in the explorer and recognition of validators on Taostats. 

The full list of these validators can be view on the Verified Validators page with more information available in the [Validators](doc:validators) section of the documentation.

<br />

## Child Hotkey Validator

A validator can use [Child Hotkeys](doc:child-hotkeys) to distribute their stake to other active validators.  This means that one can be a "validator" without running any infrastructure on  Bittensor subnets.