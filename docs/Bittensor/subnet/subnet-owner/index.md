---
title: Subnet Owner
excerpt: >-
  A group or organisation that owns the key to and controls the codebase of a
  subnet
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
If you have an idea for the creation of a decentralised machine learning or commodity through a novel validation and incentive mechanism design, you can build a subnetwork for Bittensor.

# Idea

What is the purpose of the subnet? What is the commodity/machine learning commodity you are looking to provide and where does it derive its value?

Everything starts with an idea or a problem to solve.

# Process

Subnet owners are responsible for providing the base miner and validator code. They also design the all important incentive mechanism on which value is assigned to miners work.

* Handling all vectors that miners or validators might use to subvert the subnet.

There are very in depth tutorials for [creating a subnet](https://docs.bittensor.com/tutorials/basic-subnet-tutorials) covered in the official Bittensor Documentation which we will not attempt to cover here, however the process deployment can be broken down as

* Running locally: Curing the initial construction phase most development teams will build locally
* Running on Bittensor testnet: Once the code base is complete and ready for testing it is possible to deploy on the Bittensor testnet which emulates a similar environment and conditions to mainet in order to refine the code and processes, deploy and support applications  and infrastrucutre and to start to introduction network participants ot the product.
* Running on Bittensor mainet: Once the subnet has proven itself on testnet and feels ready to deploy on mainet then the registration fee must be locked up and the subnet becomes live on the main Bittensor network with an immunity period of 7 days.

# Registration

To register a subnet, the subnet owner must pay the lock cost. This tao is burned and is no longer returned to the SN owner.

Once a new subnet is registered, Emissions are turned off to allow the SN owner some time to test their code, and work through any kinks in their framework.  When the SN owner is ready to start their subnet, they call the `start_call` extrinsic to turn on emission to their subnet.

> 📘 When in startup mode
>
> * Set your identity on the chain `btcli s set-identity`
> * The owner hotkey (UID 0) will have the same address as your coldkey.  Do a hotkey swap.
> * Test validation. Make sure your validator can set weights, and is doing so on the regular. UID 0 is a good place for you validator.  You'll receive your owner rewards and validation rewards to the same hotkey.
> * Do you allow Neuron registration before you begin emission?

Note that Subnets that are registered, but have not started the subnet will have 0 emission.

Have a great subnet idea?  Read our [Subnet Creation Best Practices](doc:subnet-creation-best-practices) for more ideas.

<br />

# Subnet Owner Neuron - 

Every subnet owner is given an immune neuron.  

## Mining

Any mining emission to this neuron is burned.

## Validation

Subnet owners are incentivized to run a validator.  They are best to judge results of the miners, and to provide access from external users to the subnet.

It is also an additional revenue stream - The 18% of owner alpha can be used as a validator, and gain additional alpha returns on the holdings.
