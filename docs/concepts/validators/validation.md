---
title: Validation
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

Validators are the neurons in a subnet that validate miner output and provide gateway access to the network

> 📘 **This section focuses on the validator architecture inside a subnet.**
>
> The [Validator Persona](/docs/validator) has details on how a validator can be run.

On each subnet there are a configurable number slots reserved for validation (default: 64). In practice, these slots are not all filled by validators, and miners can use these slots as well.

Validators have three primary roles. Two exist inside each subnet mechanism, and the third is distribute stakeholder emission.

1. **Validation of miner output**.  This is usually done by sending regular requests to each miner and then assigning a value/score to the response.  These scores are often added to a moving average of the miners performance which enables a score (weights) to be set at regular intervals on the blockchain for all miners by that validator. These weights form part of the incentive landscape which when combined with the weights of the other validators using [Yuma Consensus](/docs/consensus) are then used to define and distribute emissions.
2. **Gateway access to the network**. The only way a user or application can query a subnet is through the hotkey of an active validator - therefore validators also act as trusted gateways to the miners which in turn allows miners to prioritise queries based on a stake.
3. **Stakeholder Emissions**. Stake is still routed through validators on each subnet.  See [Dividends for Validators](/docs/dividends-for-validators), [Emissions: Root vs. Alpha Stake](/docs/stakeholder-emissions-root-vs-alpha) for further details.

The amount of tao a validator has as delegated stake defines both the value of the weights they set for miners and as a result allows for a natural market prioritisation of access to form.

Validators must assess how well the miners are performing and the value they create on the network.  Each subnet has a different [Incentive Mechanism](/docs/incentive-mechanisms) for determining how the validator interacts with the miner and scores the responses.

The incentive mechanism is not fixed and it is the possibility for design of unique and innovative incentive mechanisms that is one of the key values of Bittensor - allowing each subnet a different approach to validation.

## Parent/Child hotkeys

Validators can share stake with other validators by becoming a parent hotkey. This allows the parent to share a percentage of stake (from 0-100%) with the child hotkey.  See [Child Hotkeys](/docs/child-hotkeys) for more details.

## Weight copying

[Weight Copying](/docs/weight-copying) occurs when a validator does not perform actual miner validation, but copies the weights of other validators.  The Bittensor team has added encrypted weights in an attempt to mitigate this issue.

## Minimum Stake

Some subnets have a minimum stake required to be a successful validator. Below this minimum value, weights set by a validator would have near zero effect on the miner's emissions.

## Validator Registration

Learn how to [register a node](/docs/node-registration) on a subnet.

In addition to the steps in the above link, validators need to have a significant amount of TAO/alpha staked to their hotkey to be successful in validating miners. This is due to market dynamics incentivising miners to naturally prioritise requests from validators with more stake as their weights hold great influence over consensus of trust.

Although this varies from subnet to subnet there is a hard floor of 1k tao with a generally accepted competitive functional floor of around 20k tao (at the time of writing). This means that whilst it is possible to validate with less than 20k tao, you may not achieve the same level of responses from all miners and as a result consensus in the weights you set, and as a result your appropriate share of emissions.

It should also be noted that in order to validate competitively on root, you must be present on as many subnets as possible.  This increases your emissions, and thus the return to the stakeholders.

> 📘 **How can miners ignore validators?**
>
> If a validator has a very low amount of tao staked, their scoring has very little weight in Consensus.   Ignoring a validator allows the miner to focus on the validators that will impact their score (and create the subnet's output).

## Validator Emission

Validators are awarded emission from the network based on their dividend score.  Dividend is evaluated from the stake and Vtrust values. Vtrust describes how well their weights match the **consensus** of other validators.  See [Dividends for Validators](/docs/dividends-for-validators) for a detailed analysis.

<Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=XUgoBN8VB7Q" href="https://www.youtube.com/watch?v=XUgoBN8VB7Q" providerUrl="https://www.youtube.com/" providerName="YouTube" />
<Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=j_Qa9inlsng" href="https://www.youtube.com/watch?v=j_Qa9inlsng" providerUrl="https://www.youtube.com/" providerName="YouTube" />
<Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=Bd4-eyGa1o0" href="https://www.youtube.com/watch?v=Bd4-eyGa1o0" providerUrl="https://www.youtube.com/" providerName="YouTube" />
<Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=GzB381fBQQM" href="https://www.youtube.com/watch?v=GzB381fBQQM" providerUrl="https://www.youtube.com/" providerName="YouTube" />
<Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=wZhgzMKc05I" href="https://www.youtube.com/watch?v=wZhgzMKc05I" providerUrl="https://www.youtube.com/" providerName="YouTube" />

# Gateway Access

As miners are only scored by validators there is no incentive for them to receive or trust requests from anyone else except a valid validator.  Any request to the miners must therefore pass through a validator which will be routed to a miner(s)  who will generate the response to the validator, who returns the response to the external user.

This allows validators to build API infrastructure or allow their access to be valued by any other network participant providing API access to the network.

This is just one way of facilitating access to the network data via a validator and constant advancements a birthing new and innovative ways to interface with the commodities produced by subnets.

<Image border={false} alt="Diagram of a validator acting as a gateway between an external user and a grid of miners, forwarding requests to a selected miner and relaying responses" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/3a9848e231734fdb.png" />
