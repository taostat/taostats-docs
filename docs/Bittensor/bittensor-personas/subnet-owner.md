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

To register a subnet, the lock-cost starts at 100 tao but increases with each subnet registration activity snd then degrades with time.  The registration cost for a subnet is unlocked and returned to the owner should the subnet be de-registered.  

Have a great subnet idea?  Read our [Subnet Creation Best Practices](doc:subnet-creation-best-practices) for more ideas.
