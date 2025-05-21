---
title: Glossary
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
# Coldkey:

The main key for a Bittensor wallet. Used to transfer, buy, sell, and stake/delegate tao.

# Commit Reveal:

Bittensor's approach to address [weight copying](#weight-copying).  A process where validators encrypt their weights for a given period - prevening weight copiers from reading their weights immediately. 

# Consensus

Miner's score from the Yuma Consensus. Not applicable to validators.

# Consensus based weights:

See [liquid alpha](#liquid-alpha) 

# Daily Rewards:

A column in the subnet metagraph. Based on the current emission - extrapolated to 24 hours.  Example: If your emission is 1 tao/epoch, your Daily reward will be 20 tao. (20 epochs/day)

# Delegate

The process of staking tao to a validator.  When tao is delegated, the owner of the tao receives a portion of the validator's emissions.

# Dividends:

A score for validators denoting the fraction of emission for each validator.

# Events:

Events are node/subnet registrations, tao trades, delegations, and distributions. They are recorded in the bittensor chain.

# Emission:

Emission describes the distribution of tao in the network.  There are two places where emission is used:

- **Subnet Emission**. In the root Subnet, emission refers to the percentage of tao to each Subnet.  For example a 10% emission means that 10% of all tao generated is sent to that subnet. 
- **Neuron Emission** Inside each subnet, all miners and validators are awarded emission (as seen in the metagraph.)  In the case of neuron emission, the value is in tao/epoch. 

When a subnet closes registration, the Subnet retains its emission percentage, but all tao is recycled - so miners and validators receive no emission.

# Extrinsic:

A grouping of events.  For example - a Balance Transfer extrinsic will have withdrawal and transfer steps.

# Halving/Halvening:

When half of the remaining blocks have been placed in circulation, the emission rate will drop by half. For example when 10.5M of the 21M blocks have been emitted (Tentatively 2026).  The Halvening is the event taking place

# Hotkey:

Hotkeys are used to register subnets and nodes on the network.  One hotkey can be registered per subnet.  All hotkeys are associated with a coldkey. Coldkeys can have multiple hotkeys.

# Incentive:

A score for miners. Calculated from consensus, the incentive demotes the portion of miner emissions to be distributed to each miner.

# Immunity:

Time period (defined in blocks) that a new node or subnet is protected from de-registration.

# Liquid Alpha:

Also know as consensus based weights.  Introduced in Bittensor 7.3, this feature changes the way Validator dividends are calculated.  The "Bond" between each validator and miner is a exponentaial moving average, where the  most recent bond is weighed at alpha = 0.9.  With Liquid alpha, this becomes a variable. Subnets with Liquid alpha enabled set the [Subnet Hyperparameters](doc:subnet-parameters) liquid_alpha_enabled to true.

# Miner:

Miners are nodes on a subnet.  Miners are given work to perform, and this work is graded by the validators.  Miners receive tao emissions as an incentive for their work. [Miner](doc:miner)

# Recycle:

Tao used to register a node is recycled - it is removed from circulation to be emitted again at a later date.  As tao is recycled, the chain halving is pushed to a later time. There are two main forms of recycle:

- Root:  All emissions sent to Root subnet are recycled. See [Root Subnet](https://docs.taostats.io/v1.1/docs/root-subnet#root-subnet-emissions)  for more details.
  - Any Subnet with neuron registration turned off will behave like the root subnet, and the tao will be recycled. 
- Neuron Registration: All fees to register miners and validators are recycled.

# Stake:

A tao owner can stake (or delegate) their tao with a validator. The higher the validator's stake, the higher their return.  Delegated tao receives a portion of the validator's tao emissions. See: [Staking/Delegation](doc:staking)

# Subnet:

Short for "subnetwork." There are currently 32 subnets in the Bittensor network. [Subnets](doc:subnets).

# Take:

The percentage of validator emissions kept by the validator.  The remaining percentage is distributed amongst delegators.  This is a variable that is set by each validator. It can range from 9-18% and can be updated once every 30 days.

# Tao:

The token of the Bittensor subtensor.  1 tao is emitted from the network every 12 seconds. Tao can be divided into rao (there are 1B rao per tao).  Learn more about [Tao](doc:tao) and [Tao Allocation](doc:tao-allocation).

# Trust

A score for miners, created by the Yuma Consensus. It is a combination of all the weights from all the validators.  Higher trust leads to higher incentive & emissions.

# Undelegate

The process of removing delegation/stake from a validator. The tao removed from the validator will be added to the user's coldkey.

# Validator:

Validators are nodes on a subnet. Validators check the work of the miners and grade the miners based on the quality of the response. [Validator](doc:validator)

# VTrust:

A score given to validators on a subnet. It is a ranking based on how well the validator's weights match the consensus. High VTrust leads to higher emissions.

# Weight copying:

When a validator copies the weights of other validators. This is sometimes done to avoid grading the miners - and thus not providing value to the Subnet.