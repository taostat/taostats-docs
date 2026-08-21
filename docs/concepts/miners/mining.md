---
title: Hardware requirements
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

Miners are nodes in a Bittensor subnet that produce output as defined by the subnet code.

> 📘 **This section focuses on the miner architecture inside a subnet.**
>
> The [Running a Miner](/docs/miner) has details on how a miner can be run.

Miners produce output as defined by the subnet code. Each Subnet completes a different type of task, so mining is unique to each subnet. As miners are only scored by validators, there is no incentive for them to receive or trust requests from anyone other than a validator, therefore all requests to the miners pass through a validator.

<Image border={false} alt="Tiered flow diagram showing user requests crossing a boundary to a validator layer, then routed to a selected miner and returned" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/962c39dcad6dc762.png" />

Mining hardware requirements vary by subnet although most require some for of GPU to perform the require compute functions.  Each subnet's github repository should have a `min_compute.yml` or information in the readme, describing the hardware requirements for mining the subnet.  Each Github repository is listed on the Subnet page on taostats.io.

# Miner Trust/Incentive

Each miner works to maximise their trust and incentive metrics on the network. This is done by meeting the validation requirements for the subnet at a higher level than their peers.  Each validator will grade the results of the miner, assigning a score.  Each epoch, the incentive scores (weights) are aggregated by the consensus mechanism to determine the miner's emissions.

See [Incentive for Miners](/docs/consensus-for-miners) for a detailed breakdown of how miner incentive is calculated.

# Miner Registration

Learn how to [register a node](/docs/node-registration) on a subnet.
