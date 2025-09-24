---
title: Subnet Architecture
excerpt: How do Subnets work?
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
The Bittensor network's primary division is into a group of subnets.  The subnets are numbered, and there is theoretically no limit to the number of subnets that can exist.

Each Subnet runs a self-contained codebase on top of the Bittensor code, each defining a unique context for the incentivised generation of value. Although each subnet is unique and runs with independent sets of participants, the interface with the Bittensor network and use of Yuma Consensus is common across all subnets. (There is also a subnet 0: the [Root Subnet](doc:root-subnet)).

# Architecture of Subnets

## Subnet Mechanisms (Formerly Subsubnets)

Each subnet has a task or mechanism that is performed by the participants.  It is now possible for subnets to have **multiple** mechanisms inside a single subnet.  These were formerly called subsubnets.

At launch:

* There will be a max of 2 subnet mechanisms can be implemented, eventually increasing to higher numbers.
* Miners and Validators can participate in all mechanisms with a single UID.
* Subnet owners can split the emission distribution amongst mechanisms (50:50, 90:10, etc.)
* Subnet emission to miners will be based on consensus/incentive on each mechanism, multiplied by the mechanism distribution.
  * 50:50 split: Miner has 2 incentives 0.1 and 0.2.  0.1 _.5 + 0.2_.5 = 0.15 incentive overall.
  * 90:10 split: Miner has 2 incentives 0.1 and 0.2.  0.1  * .9 + 0.2*.1 = 0.11 incentive overall.
* Subnet emission to validators will be based on Vtrust and Dividends in each subnet mechanism, multipled by the mechanism distribution.

## Mechanism architecture

Subnets generally have 256 <Glossary>neurons</Glossary> (Subnets 0 and 1 are exceptions to this rule), set in the subnet [hyperparameters]().  In time, this will be a custom configurable value.

The neurons are a mix of validators and miners with 64 slots reserved for validators and the remainder slots reserved for miners.  If validator slots are left unused they can be utilised by miners.  In practice, most subnets have 5-15 validators, and the remaining  slots are used by miners.

> 👍 Nervous System Analogy
>
> As you dig deeper into Bittensor and AI you will come across vocabulary references to the nervous system such as neurons. Neurons have axons, dendrites and synapses.  Since neurons are the way the nervous system transmits data, it is a convenient analogy to describe how data is transmitted through the subnet.
>
> Easy mode:
>
> * **Neurons** are nodes or servers running on a subnet.
> * **Synapse**: Data sent between neurons
> * **Axons**: receives message (server). The neuron's IP:port is considered the axon.
> * **Dendrite**: sends message (client)

### Validators

Validators are nodes in the subnet that perform two roles.

1. **Validation of miner output**.  This is typically done by sending regular requests to each miner and then assigning a value/score to the response.  These scores are usually added to a moving average of the miners performance which enables a score (weights) to be set at regular intervals on the blockchain for all miners by that validator. These weights form part of the incentive landscape which when combined with the weights of the other validators using [Yuma Consensus](doc:consensus) are then used to define and distribute emissions.
2. **Gateway access to the network**. The only way a user or application can query a subnet is through the hotkey of an active validator - therefore validators also act as trusted gateways to the miners which in turn allows miners to prioritise queries based on a stake.

#### Delegated Stake

Tao holders can stake their tao with validators. Validators with higher stake receive higher emissions (that are shared with the stakeholders).  The weights set by validators is also influenced by the amount of stake held. The amount of tao a validator has as delegated stake defines both the value of the weights they set for miners and as a result allows for a natural market prioritisation of access to form.

* [Validator (Architecture)](doc:validation)
* [Validator (Persona)](doc:validator)
* [Emissions for Validators](doc:incentive-for-validators)

<br />

### Miners

Miners produce output as defined by the subnet code. This work is usually performed by running code in order to complete tasks.  Each subnet has differnet mechanisms, requiring different expertises and hardware.  Although the mechanisms can vary from subnet to subnet, the power of distributed compute is one of the key values of the network. The validators then request this output for both the rewards mechanism and to satisfy any external queries.

Miners are ranked by validators and given an incentive score.  Miners with higher incentive values receive higher <Glossary>emissions</Glossary>.

* [Miner (Architecture)](doc:mining)
* [Miner (Persona)](doc:miner)
* [Emission for Miners](doc:consensus-for-miners)

### Consensus

Each subnet undertakes a specific task. In order to evaluate how the task is being performed, an incentive mechanism is used by validators to evaluate work performed by the miners.  The validators score each miner, and set weights on-chain each epoch. These weights are aggregated by [Yuma Consensus](doc:consensus) to form an overall incentive landscape upon which trust values are calculated to determine emissions.

<br />

# Subnet Registration

Anyone can register a new subnet provided they have a wallet containing the current subnet registration cost in tao.  Once a Subnet is registered, it set to an inactive state. This period allows the new subnet to iron out the last steps, and begin building relationships with miners and validators. There is no emission when a subnet is inactive.

In practice, many subnets build in the testnet prior to going "live" on the main bittensor chain. This allows miners and validators to test out the code, and find any issues that might arise. It also allows the subnet team to build awareness of the project, ensuring faster acceptance on chain, and (hopefully) higher emissions.

## Subnet Pool at registration

When a new subnet is registered, the [Subnet Pool](doc:subnet-pools) will be initialized with:

* 1 alpha
* 1 tao

It is currently possible to buy and sell alpha in an inactive Subnet.  There is **very low** liquidity in these pools, so only invest here if you know what you are doing.

## Registration Cost

There is a cost to register a new subnet.  The cost for a new registration is based on the demand of subnets - more frequent registrations raise the cost, and then the cost goes down lover time. A portion of the lock cost is paid into the [Subnet Pools](doc:subnet-pools). The remainder is recycled.

You can determine the current price using the [Bittensor CLI](doc:command-line-tool):

```
btcli subnet lock_cost
>> Subnet lock cost: τ3,796.780457067
```

Or you can view a historical chart of registration cost at <a href="<https://taostats.io/subnets>" target="_blank">Taostats</a>.

<Image align="center" alt="A screenshot of the Subnet registration cost over time." border={false} caption="A screenshot of the Subnet registration cost over time." src="https://files.readme.io/dc48e04eec3d2bbe2b7a19c012073d38b4b40461a174098dedf42edc32e77292-Screenshot_2024-09-03_at_17.35.05.jpg" />

## Subnet immunity

New subnets have 4 months of immunity from being de-registered.

## Subnet activation

New subnets are default not active, and receive no emission.  After 7 days, the subnet owner can "turn on" the subnet, starting emission, and letting validators and miners begin earning emission.

# Subnet Emission

See [Subnet Emission tao and alpha](doc:subnet-emissions)

<br />

# Subnet de-registration

In september 2025, subnet deregistration was readded.  The subnet with the lowest moving average price will be deregistered when a new subnet is created.

* All alpha is liquidated.  All holders of alpha will be given a weighted % of the tao remaining in the subnet pool. This will appear on their coldkey, as unstaked tao.
* The new subnet will take over the netuid.
