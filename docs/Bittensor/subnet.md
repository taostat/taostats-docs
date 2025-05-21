---
title: Subnet Architecture
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
The Bittensor network's primary division is into a group of subnets.  The subnets are numbered, and there is theorietically no limit to the number that can exists.  

Each Subnet runs a self-contained codebase on top of the Bittensor code, each defining a unique context for the incentivised generation of value. Although each subnet is unique and runs with independent sets of participants, the interface with the Bittensor network and use of Yuma Consensus is common across all subnets. (There is also a subnet 0: the [Root Subnet](doc:root-subnet)).

> 📘 If a new Subnet is registered (and there are no empty subnet slots), the Subnet with the lowest emission not in immunity is ejected.  Learn more about [Subnet Registration](#Subnet-Registration)

# Architecture of Subnets

Subnets generally have 256 <<glossary:neurons>> (Subnets 0 and 1 are exceptions to this rule), set in the subnet [hyperparameters](<>).  In time, this will be a custom configurable value. 

The neurons are a mix of validators and miners with 64 slots reserved for validators and the remainder slots reserved for miners.  If validator slots are left unused they can be utilised by miners.  In practice, most subnets have around 20 validators, and the remaining 246 slots are used by miners.

> 👍 Nervous System Analogy
> 
> As you dig deeper into Bittensor and AI you will come across vocabulary references to the nervous system such as neurons. Neurons have axons, dendrites and synapses.  Since neurons are the way the nervous system transmits data, it is a convenient analogy to describe how data is transmitted through the subnet.
> 
> Easy mode: 
> 
> - **Neurons** are nodes or servers running on a subnet.
> - **Synapse**: Data sent between neurons
> - **Axons**: receives message (server). The neuron's IP:port is considered the axon.
> - **Dendrite**: sends message (client)
> 
> For a deeper discussion of biology and nodes see: TODO

## Validators

Validators are nodes in the subnet that perform two roles.

1. **Validation of miner output**.  This is typically done by sending regular requests to each miner and then assigning a value/score to the response.  These scores are usually added to a moving average of the miners performance which enables a score (weights) to be set at regular intervals on the blockchain for all miners by that validator. These weights form part of the incentive landscape which when combined with the weights of the other validators using [Yuma Consensus](doc:consensus) are then used to define and distribute emissions.
2. **Gateway access to the network**. The only way a user or application can query a subnet is through the hotkey of an active validator - therefore validators also act as trusted gateways to the miners which in turn allows miners to prioritise queries based on a stake.

### Delegated Stake

Tao holders can stake their tao with validators. Validators with higher stake receive higher emissions (that are shared with the stakeholders).  The weights set by validators is also influenced by the amount of stake held.The amount of tao a validator has as delegated stake defines both the value of the weights they set for miners and as a result allows for a natural market prioritisation of access to form. 

- [Validator (Architecture)](doc:validation)
- [Validator (Persona)](doc:validator)
- [Emissions for Validators](doc:incentive-for-validators)

<br />

<br />

## Miners

Miners produce output as defined by the subnet code. This work is usually performed by running code in order to complete tasks.  Each subnet has differnet mechanisms, requiring different expertises and hardware.  Although the mechanisms can vary from subnet to subnet, the power of distributed compute is one of the key values of the network. The validators then request this output for both the rewards mechanism and to satisfy any external queries. 

Miners are ranked by validators and given an incentive score.  Miners with higher incentive values receive higher <<glossary:emissions>>.

- [Miner (Architecture)](doc:mining)
- [Miner (Persona)](doc:miner)
- [Emission for Miners](doc:consensus-for-miners)

## Consensus

Each subnet undertakes a specific task. In order to evaluate how the task is being performed, an incentive mechanism is used by validators to evaluate work performed by the miners.  The validators score each miner, and set weights on-chain each epoch. These weights are aggregated by [Yuma Consensus](doc:consensus) to form an overall incentive landscape upon which trust values are calculated to determine emissions.  

<br />

# Subnet Registration

Anyone can register a new subnet provided they have a wallet containing the current subnet registration cost in tao.  Once a Subnet is registered, it is given <<glossary:immunity>> from de-registration for 7 days. The period of immunity allows the new subnet to build trust and establish emissions without being de-registered in the event or further subnet registrations.

In practice, many subnets build in the testnet prior to going "live" on the main bittensor chain. This allows miners and validators to test out the code, and find any issues that might arise. It also allows the subnet team to build awareness of the project, ensuring faster acceptance on chain, and (hopefully) higher emissions.

## Subnet Pool at registration

When a new subnet is registered, the [Subnet Pool](doc:subnet-pools) will be initialized with:

- 1 alpha
- {subnet count} alpha

## Registration Cost

There is a cost to register a new subnet.  The cost for a new registration is based on the demand of subnets - more frequent registrations raise the cost, and then the cost goes down lover time. A portion of the lock cost is paid into the [Subnet Pools](doc:subnet-pools). The remainder is recycled.

You can determine the current price using the [Bittensor CLI](doc:command-line-tool):

```
btcli subnet lock_cost
>> Subnet lock cost: τ3,796.780457067
```

Or you can view a historical chart of registration cost at <a href="<https://taostats.io/subnets>" target="_blank">Taostats</a>.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/dc48e04eec3d2bbe2b7a19c012073d38b4b40461a174098dedf42edc32e77292-Screenshot_2024-09-03_at_17.35.05.jpg",
        null,
        "A screenshot of the Subnet registration cost over time."
      ],
      "align": "center",
      "caption": "A screenshot of the Subnet registration cost over time."
    }
  ]
}
[/block]


<br />

# Subnet Emission

See [Subnet Emission tao and alpha](doc:subnet-emissions)

<br />

# Subnet de-registration

in dTao, subnets can no longer be deregistered.