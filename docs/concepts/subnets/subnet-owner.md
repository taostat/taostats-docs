---
title: Idea
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

A group or organisation that owns the key to and controls the codebase of a subnet

If you have an idea for the creation of a decentralised machine learning or commodity through a novel validation and incentive mechanism design, you can build a subnetwork for Bittensor.

What is the purpose of the subnet? What is the commodity/machine learning commodity you are looking to provide and where does it derive its value?

Everything starts with an idea or a problem to solve.

# Process

Subnet owners are responsible for providing the base miner and validator code. They also design the all important incentive mechanism on which value is assigned to miners work.

* Handling all vectors that miners or validators might use to subvert the subnet.

There are very in depth tutorials for [creating a subnet](https://docs.bittensor.com/tutorials/basic-subnet-tutorials) covered in the official Bittensor Documentation which we will not attempt to cover here, however the process deployment can be broken down as

* Running locally: During the initial construction phase most development teams will build locally.
* Running on Bittensor testnet: Once the code base is complete and ready for testing it is possible to deploy on the Bittensor testnet, which emulates a similar environment and conditions to mainnet, in order to refine the code and processes, deploy and support applications and infrastructure, and to start introducing network participants to the product.
* Running on Bittensor mainnet: Once the subnet has proven itself on testnet and feels ready to deploy on mainnet, the registration fee must be locked up and the subnet becomes live on the main Bittensor network. Newly registered UIDs have an immunity period (currently around 4 months, governed by the subnet's `ImmunityPeriod` hyperparameter) before they can be deregistered by having the lowest stake-weighted score.

# Registration

To register a subnet, the subnet owner must pay the lock cost. A portion seeds the subnet pool; the remainder is recycled. It is not returned to the owner.

Once a new subnet is registered, Emissions are turned off to allow the SN owner some time to test their code, and work through any kinks in their framework.  When the SN owner is ready to start their subnet, they call the `start_call` extrinsic to turn on emission to their subnet.

> 📘 **When in startup mode**
>
> * Set your identity on the chain `btcli s set-identity`
> * The owner hotkey (UID 0) will have the same address as your coldkey.  Do a hotkey swap.
> * Test validation. Make sure your validator can set weights, and is doing so on the regular. UID 0 is a good place for you validator.  You'll receive your owner rewards and validation rewards to the same hotkey.
> * Do you allow Neuron registration before you begin emission?

Note that Subnets that are registered, but have not started the subnet will have 0 emission.

Have a great subnet idea? Read the [Subnet Owner Startup Guide](/docs/subnet-owner-startup-guide) for design frameworks, incentive-mechanism resources, and the post-registration launch checklist.

# Subnet Owner Neuron

Every subnet owner is given an immune neuron (UID 0 by default).

## Mining

The owner cannot run a miner on this hotkey to receive alpha. Any incentive (mining) emission directed to an owner or owner-immune hotkey is withheld from the miner pool — it does not pay alpha to the owner — and counts toward the subnet's `MinerBurned` proportion the following tempo, reducing the subnet's chain emission share.

Whether the subnet's `RecycleOrBurn` configuration recycles or burns the withheld emission, the penalty applies identically. There is no toggle that lets an owner recover that incentive as alpha.

See [Price-based emission shares](/docs/price-based-emission-shares) for the full `MinerBurned` mechanic.

## Validation

Subnet owners are incentivized to run a validator. They are best placed to judge miner results and to provide access to the subnet for external users.

It is also an additional revenue stream — the 18% owner alpha can be staked to a validator and earn additional alpha returns on the holdings.
