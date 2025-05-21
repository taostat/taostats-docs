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
The Bittensor network currently consists of (but is not limited to) 36 subnets.  (There is also a subnet 0: the [Root Subnet](doc:root-subnet)). The number of subnets will be expanded as the network grows.

> 📘 In May-July 2024, the number of subnets will grow from 32 to 64 at a rate of 4 new subnets a week.

Each Subnet runs a self-contained codebase on top of the Bittensor code, each defining a unique context for the incentivised generation of value. Although each subnet is unique and runs with independent sets of participants, the interface with the Bittensor network and use of Yuma Consensus is common across all subnets.

> 📘 If a new Subnet is registered (and there are no empty subnet slots), the Subnet with the lowest emission not in immunity is ejected.  Learn more about [Subnet Registration](#Subnet-Registration)

# Architecture of Subnets

Subnets currently have 256 <<glossary:neurons>> (Subnets 0 and 1 are exceptions to this rule), set in the subnet hyperparameters and will in time be a custom configurable value. 

The neurons are a mix of validators and miners with 64 slots reserved for validators (given vpermit) and the remainder for miners.  If validator slots are left unused they can be utilised by miners, ordered by the amount of tao staked on they key.

> 👍 Nervous System Analogy
> 
> As you dig deeper into Bittensor and AI you will come across vocabulary references to the nervous system such as neurons. Neurons have axons, dendrites and synapses.  Since neurons are the way the nervous system transmits data, it is a convenient analogy to describe how data is transmitted through the subnet.
> 
> Easy mode: 
> 
> - **Neurons** are nodes or servers running on a subnet.
> - **Synapse**: Data sent between neurons
> - **Axons**: receives message (server)
> - **Dendrite**: sends message (client)
> 
> For a deeper discussion of biology and nodes see: TODO

## Validators

Validators are nodes in the subnet that perform two roles.

1. **Validation of miner output**.  This is usually done by sending regular requests to each miner and then assigning a value/score to the response.  These scores are usually added to a moving average of the miners performance which enables a score (weights) to be set at regular intervals on the blockchain for all miners by that validator. These weights form part of the incentive landscape which when combined with the weights of the other validators using [Yuma Consensus](doc:consensus) are then used to define and distribute emissions.
2. **Gateway access to the network**. The only way a user or application can query a subnet is through the hotkey of an active validator - therefore validators also act as trusted gateways to the miners which in turn allows miners to prioritise queries based on a stake.

The amount of tao a validator has as delegated stake defines both the value of the weights they set for miners and as a result allows for a natural market prioritisation of access to form. 

## Miners

Miners produce output as defined by the subnet code. This work is usually performed by running GPUs in order to complete tasks and although the mechanisms can vary from subnet to subnet, it is the power of distributed compute that one of the key values of the network. The validators then request this output for both the rewards mechanism and to satisfy any external queries. 

Miners are ranked by the <<glossary:trust>>.  Miners with higher trust values receive higher <<glossary:incentive>> and as a result more <<glossary:emissions>>.

## Consensus

Each subnet has a task that is undertaken, and an incentive mechanism that can be evaluated by the validators.  The validators score each miner, and set weights on-chain each epoch. These weights are aggregated by [Yuma Consensus](doc:consensus) to form an overall incentive landscape upon which trust values are calculated to determine emissions.  

# Subnet Registration

Anyone can register a new subnet provided they have an address that contains the current subnet registration cost in tao.  Once a Subnet is registered, it is given <<glossary:immunity>> from de-registration for 7 days. The period of immunity allows the new subnet to build trust and establish emissions without being de-registered in the event or further subnet registrations.

## Registration Cost

There is a cost to register a new subnet.  The base cost is 100 tao however after a subnet is registered the cost doubles, and slowly falls back over time until the next registration or returning to the base value of 100.  On each subsequent registration the cost once again doubles from its value at the time of registration. The fee to register a subnet is locked (not spent, burned or recycled) and is returned to the address if and when the subnet is de-registered.

You can determine the current price using the [Bittensor CLI](doc:command-line-tool):

```
btcli subnet lock_cost
>> Subnet lock cost: τ100.000000000
```

Or you can view a historical chart of registration cost at <a href="https://taostats.io/" target="_blank">Taostats</a>. The chart is called "subnet registration data." In this chart, a flurry of subnet registrations had recently occurred, leading to an increase in registration costs - showing 598 TAO.:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/816b1c7-image.png",
        null,
        "A screenshot of the Subnet registration cost over time."
      ],
      "align": "center",
      "caption": "A screenshot of the Subnet registration cost over time."
    }
  ]
}
[/block]


# Subnet de-registration

With a limit on the number of subnets, (assuming all slots are filled) when a new subnet is registered an existing subnet must be de-registered. The subnet with the lowest emissions (that is not in <<glossary:immunity>>) will be removed from the network.  This means that the subnet numbers are not a chronological summary of the Bittensor network. Taostats has a [chart showing the emissions for all subnets that can be sorted low -> high](https://x.taostats.io/?_gl=1*1poggmz*_ga*NDEyNDE1Nzg2LjE3MDU1MDQ0MTE.*_ga_VCM7H6TDR4*MTcwNTY5MDI3MC44LjEuMTcwNTY5MDU3Mi4wLjAuMA..#subnets).

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/dbde2e1-image.png",
        null,
        "In this screenshot, the three lowest emission subnets have immunity, meaning that subnet 29 would be the next deregistered subnet."
      ],
      "align": "center",
      "caption": "In this screenshot from 20th January, the three lowest emission subnets have immunity, meaning that subnet 29 would be the next deregistered subnet."
    }
  ]
}
[/block]


> 📘 If a Subnet is de-registered, all node hotkeys (miners & validators) are deregistered as well.

<br />

> 🚧 Should there be a need to manually deregister a subnet these are instructions sourced from the Official Discord server.  These are untested by the Taostats team.
> 
> In order to dissolve your network , you need to call the dissolve_network extrinsic directly from polkadot.js , as we dont expose this functionality via the cli.
> 
> Here's a step by step guide to do this on polkadot.js
> 
> Connect to the Subtensor Network:  
> Open your web browser and navigate to the Polkadot.js Apps website (<https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Fentrypoint-finney.opentensor.ai%3A443#/extrinsics>).
> 
> Navigate to the Extrinsics Page:  
> In the top navigation menu, click on the "Developer" tab.  
> In the sub-menu, click on "Extrinsics" to open the Extrinsics page.
> 
> Select the subtensor Pallet:  
> On the Extrinsics page, you will see a section labeled "submit the following extrinsic".  
> In the first dropdown menu labeled "selected call", choose the subtensor pallet.
> 
> Choose the dissolve_network Function:  
> After selecting the subtensor pallet, the second dropdown menu will show the available functions within that pallet.  
> Scroll down and select the  dissolve_network function.
> 
> Provide the Required Arguments:  
> Once you've selected the dissolve_network function, you will see input fields for the required arguments.  
> For the origin argument, select the appropriate account from the "using the selected account" dropdown. This account should have the necessary permissions to dissolve the network.  
> For the netuid argument, enter the unique identifier of the network you want to dissolve. This should be a 16-bit unsigned integer. (i.e. your subnet number)
> 
> Submit the Transaction:  
> Double-check that you've entered the correct  netuid  value.  
> Scroll down to the bottom of the page and click on the "Submit Transaction" button.  
> Polkadot.js will prompt you to sign the transaction using the selected account.  
> After signing the transaction, it will be broadcast to the Subtensor network.
> 
> Monitor the Transaction Status:  
> After submitting the transaction, you can monitor its status in the "Explorer" tab of Polkadot.js Apps.  
> In the "Explorer" tab, click on the "Node Info" sub-menu to see the recent blocks and transactions.  
> Look for your transaction in the list and click on it to view its details and status.  
> If the transaction is successful, the network with the specified netuid will be dissolved, and the associated data will be removed from the Subtensor storage.