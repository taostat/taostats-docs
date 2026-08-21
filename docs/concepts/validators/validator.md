---
title: Subnet Validation
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

A validator's performance in a subnet is measured through their consensus with the other validators, measured by the vtrust metric, attained through the process of scoring and setting weights to the miners. Validators whose scores are in agreement/consensus with the rest of the validators have a higher vtrust and as a result earn more performant rewards.

> 📘 **TL;dr of successful validation**
>
> 1. The more stake your validator has - the higher the dividends/emission in each subnet.
>    1. Many subnets have minimum stake requirements — a hard floor of 1k tao, with a generally accepted competitive functional floor of around 20k tao.
> 2. For the highest stakeholder return, you must validate on as many subnets as possible - returns are additive across subnets.
>    1. Take & child take can be manipulated in each subnet to maximize returns.

Each subnet uses a unique validation and rewards mechanism to define the value of the commodity being produced and assign incentive rewards for this process. Miners complete tasks based on the subnet mechanism requirements and the validators verify, compare and score the responses. The scores are collated, normalised and submitted as weights for consensus, published to the blockchain.

The output of the consensus (rewards landscape) is the breakdown of the rewards for the validators, miners, and subnet owners. These results are recorded on the blockchain.

To see a validator's results in Taostats, [Taostats Validator pages](https://taostats.io/validators) have a wealth of detail:

<Image border={false} alt="Taostats validator list table with rank, name/address, dominance, nominators, weights, root and alpha stake, take, and a root/alpha split bar, plus search and CSV controls" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/634f60ec07588cc9.png" />

Each validator has a page with a table showing subnet-specific data:

<Image border={false} alt="Per-validator subnet table with netuid, hotkey, take, proportion, subnet and family weight/balance split bars, dominance, dividends, and trust columns" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/ec1d9d5f29f8faba.png" />

See [Taostats: For Validators](/docs/validators) for more details

# Stake/delegation

Validators are incentivised to add value to the Bittensor ecosystem. This value is recognised and rewarded by participants delegating [Stake](/docs/staking) to their validator(s) of choice. The more stake a validator has, the greater proportion of network bandwidth is afforded to them through the natural market effect of their weights holding higher value to miners as a result of the prioritisation of stake by Yuma Consensus. (Higher stake also maximises emissions for the validator.)

To reward those that stake on a validator, the validator's emissions are divided amongst all delegators.

# Emissions

Validators on each subnet receive 41% of all emissions. This is divided amongst the validators based upon their current performance on a given subnet. The dividend metric is the fraction of validator emission for each validator. It is determined from the vtrust metric, proportional to the total stake they hold on any given subnet. Validators with high VTrust and high stake will maximise returns.

## Child Take

If the validator has an active neuron, they can set a child take - if another validator places a parent hotkey on the validator's neuron, the child hotkey is awarded a percentage of their award.

## Take

As emission is divided to delegators, the validator can take a small percentage of the emissions. This is called the `take`. Today, validators can set this percentage (using the [Command Line Interface (CLI)](/docs/command-line-tool)) to be any value from 0-18% (the default value is 18%).

See the [Subnet emission overview](/docs/split-alpha-out) for a model of the percentages a validator can earn.

The remainder of the emission is distributed to the stakeholders.

## Child Hotkey Validator

A validator can use [Child Hotkeys](/docs/child-hotkeys) to distribute their stake to other active validators. This means that one can be a "validator" without running any infrastructure on Bittensor subnets.
