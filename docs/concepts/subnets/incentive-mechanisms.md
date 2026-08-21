---
title: Incentive Mechanisms
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

A subnet's **incentive mechanism** is the rule set its validators use to score miners. It is the economic heart of a subnet: it defines what "good work" means, and — through the weights validators set — it decides how the subnet's emissions flow to the miners producing that work.

Every subnet on Bittensor designs its own incentive mechanism. There is no single, network-wide scoring rule. A language-model subnet, a compute subnet, and a prediction-market subnet each reward completely different behaviour, so each writes its own mechanism.

## How an incentive mechanism works

An incentive mechanism runs as a continuous loop between the miners and validators of a subnet:

1. **Miners produce work.** Each miner responds to the subnet's task — generating text, serving inference, returning a prediction, storing data, or whatever commodity the subnet produces.
2. **Validators evaluate that work.** Validators send challenges to miners and score the responses against the subnet's definition of quality. Scoring logic lives in the subnet's own validator code, not in the chain.
3. **Validators set weights.** Each validator converts its scores into a vector of **weights** — one number per miner — and submits it on-chain. A higher weight means "this miner did more of the work I value."
4. **Consensus turns weights into emissions.** The Yuma consensus mechanism combines every validator's weights, discounts outliers and dishonest weight-setting, and produces the network's agreed ranking. That consensus ranking determines each miner's share of the subnet's emissions.
5. **Emissions are paid, and the loop repeats.** Miners earn alpha emissions in proportion to the consensus weight they hold, giving them a direct incentive to keep producing the work the mechanism rewards.

For the mechanics of how weights become emissions, see [Consensus](/docs/consensus) and [Validation](/docs/validation).

## What makes a good incentive mechanism

A well-designed mechanism has three properties:

* **It rewards the behaviour the subnet actually wants.** The score a miner earns should track real value produced, not a proxy that is easy to satisfy without doing the work.
* **It is expensive to game and cheap to verify.** Validators should be able to check a response far more cheaply than a miner can fake a good one. When faking is cheaper than working, miners optimise for the fake.
* **It resists collusion.** Because emissions follow consensus weights, a mechanism has to survive validators or miners trying to coordinate for unearned rewards.

> 📘 The most common failure mode is **[weight copying](/docs/weight-copying)** — a validator that copies another validator's weights instead of doing its own evaluation. It earns dividends without contributing honest scoring, which degrades the signal the whole mechanism depends on. Yuma consensus and mechanisms such as commit–reveal are designed to blunt this.

## Where the mechanism lives

The incentive mechanism is **off-chain code** written by the subnet owner and run by that subnet's validators and miners — typically published in the subnet's GitHub repository. The chain does not define the scoring rule; it only records the weights validators submit and runs [consensus](/docs/consensus) over them. This is why two subnets can share the same chain and consensus while rewarding entirely different work.

Changing a subnet's incentive mechanism is one of the most consequential things a [subnet owner](/docs/subnet-owner) can do: it changes what every miner is optimising for.

## Related

* [Consensus](/docs/consensus) — how weights become emissions (Yuma)
* [Validation](/docs/validation) — the validator's role in scoring
* [Weight copying](/docs/weight-copying) — the main gaming vector
* [Subnet emissions](/docs/subnet-emissions) — where the rewarded emissions come from
* [Subnet owner](/docs/subnet-owner) — who designs the mechanism
