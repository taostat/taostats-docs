---
title: Starting as a Miner
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
TL;dr: It's complicated, and you're going to have to do some research.

TL;dr 2:Mining on Bittensor is very competitive. May the odds be ever in your favor.

# Introduction

So you want to mine. What is the best way to mine? How do I get started? Can i mine with \<hardware configuration>?

<Image border={false} src="https://files.readme.io/a1aa463bb9f5e3ae126baf78021660bc7b0592ac80ce0844ff819ec7d44fd0e0-image.png" />

# The Basics

* [Miner (Architecture)](doc:mining): Interaction to mining on Bittensor.
* [Emission for Miners](doc:consensus-for-miners) : How you are rewarded with emissions.
* [Taostats: For Miners](doc:taostats-for-miners) How do you visualize how your miner is doing.

<br />

# Picking a Subnet

There are multiple subnets on Bittensor (October 2024 - 52 subnets). Each subnet has a different objective, goal - and this each has different mining/validation requirements.

### Picking a subnet

* What are you interested in? If it is model-training, sports or finance predictions, compute, biology, astrophysics.. there may be a subnet that matches your interests.
  * Each subnet has a Github repository and a channel in the Bittensor Discord.
* Your hardware- You may already have HW. Check each SN's hardware requirements.
* Emissions: Miners are awarded a proportion of the subnet's emissions

> 📘 Should I go for a high emission subnet?
>
> # Option 1: Go for the big bucks
>
> Subnet xx has the highest emission amongst all the subnets.
>
> Some of the original subnets have very high emission. But they have also been around for 6 months-2 years. Some of the miners on this subnet have had 11 months to modify and improve their miners. Using the default miner is unlikely to beat these highly tuned models. Prepare for a lot of coding, trial & error.
>
> # Option 2: Start with a new Subnet
>
> Subnet XX was registered this week. Its emissions are very small (the top miner is making $1.50/day). But, There are just 9 miners active (and 256 slots). So your miner will not be deregistered, and you can learn how to maximize your returns on the subnet along with everyone else. You may have small returns at the start, but if you believe the subnet can succeed - you may be an insider on the _next_ biggest subnet.

* Registration cost: Each subnet has different cost to register a neuron. [Taostats: For Miners](doc:taostats-for-miners) shows how to determine the cost and how it changes over time.
* Is there a testnet? If you can run on a testnet - you can forego the registration costs to see if you are able to run the miner.  You can also run a local blockchain for testing.

# Skills required

* DevOps: You will be running at least one server to be an active miner.
* Coding: You will need to optimize your miner to fit the requirements of the subnet. Most of the subnets are written in Python.
* Subnet specific skills: Perhaps understanding inference models or Protein folding.
