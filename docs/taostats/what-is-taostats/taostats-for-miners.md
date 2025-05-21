---
title: 'Taostats: For Miners'
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
If you are thinking about mining on Bittensor - or you want to improve your mining nodes, Taostats has a wealth of information to help you get started.

> 🚧 The current views in Taostats are designed for validators. Miner specific views are *coming soon*.

# Getting started: the data

When looking at your miner's activity in taostats - there are probably a few different ways you want to interact:

1. [The metagraph](https://docs.taostats.io/docs/taostats-for-miners#the-metagraph-for-miners) to see how your miner(s) are doing in relation to the other neurons.
2. [Coldkey view](doc:coldkey-view): A view of all your miners in one place.
3. [Hotkey view](doc:hotkey-page): A detailed view of a specific miner.

<br />

# The metagraph: for miners

Each subnet publishes a Metagraph - a giant table of data about each node. See [Subnet Metagraph table](doc:metagraph#miner-view) for details on how to best sort the metagraph, and how to read the data.

The columns most relevant to miners are *trust*, *incentive* and *emission*.

* Trust: Scored by validators on how "trustworthy" your results are. What this means varies from Subnet to Subnet.
* Incentive: The percentage of miner emission that will be awarded to each validator. The sum of this column is 1.
* Emission: This is the tao awarded each epoch. This is calculated from the incentive and the miner's share of emissions. Note that Emission is shown *per epoch*, or 360 blocks.
* Daily tao: Emission \*20 (\~ 20 epochs per day). Note: This is an instantaneous calculation - not a predictor.
* Daily$: is daily tao \* current price of tao. Note: This is an instantaneous calculation - not a predictor.

<br />

# ColdKey View

The [Coldkey view](doc:coldkey-view) in taostats will show details about a specific coldkey wallet, including details about any active hotkeys.

<br />

# Registering a node

To mine, you need to know how competitive a subnet is, how much it costs to register a node on the subnet, and how the subnet distributes emissions to miners. Register a node using the [Command Line Tool](doc:command-line-tool)"

```
btcli subnet register
```

## Subnet emissions

Each subnet is granted a percentage of the blockchain [emission](doc:subnets-emission). High-emission subnets are more profitable, but also more competitive. Miners receive 41% of the emission for the subnet. The emission for each subnet can be found in multiple places in taostats:

* Subnet pages

  <Image align="center" width="20%" src="https://files.readme.io/5cfea15-image.png" />
* [https://x.taostats.io/subnets](https://x.taostats.io/subnets)

![](https://files.readme.io/2f84759-image.png)

* [taostats.io](taostats.io) homepage:

![](https://files.readme.io/4fef6cf-image.png)

<br />

## Miner Incentive distribution

Subnets with higher emissions tend to be more competitive for miners, meaning that the risk of being deregistered is high. The competitiveness of a subnet can be seen on subnet[individual subnets distribution graphs](https://taostats.io/subnets/netuid-19/#distribution). For example:

<Image alt="Snapshot of Subnet 13" align="center" src="https://files.readme.io/dd631f9-image.png">
  Subnet with a wide distribution
</Image>

<Image alt="Snapshot of subnet 19" align="center" src="https://files.readme.io/59974ba-image.png">
  subnet with a narrow distribution
</Image>

In the first screenshot, there is a large distribution of emissions. In this subnet, a well-performing miner can keep above the threshold for de-registration.

In the second screenshot, the range for Active keys is very narrow (0.00401 - 0.00441). Any minor disruption to your miner may cause you to fall to the bottom of the emissions chart and be deregistered.

## Node Registration cost

You can view the current registration cost at [https://taostats.io/subnets/netuid-`<subnetID>`/#registration](https://taostats.io/subnets/netuid-19/#registration). Competitive subnets generally cost more to register a node than non-competitive nodes.

### Deregistration

![](https://files.readme.io/8721c65-image.png)

<br />

When a new miner is registered, the lowest miner out of immunity is deregistered. Any new miner should aim to be above the last deregistration incentive before they exit immunity.

<br />

## Immunity period

Each new node is granted immunity for a defined number of blocks. When you have immunity, you cannot be de-registered. The [Node Registration](https://taostats.readme.io/docs/node-registration) page describes how to use the BTCLI to determine a subnet's immunity period.

## Emission Distribution

Some subnets evenly distribute emissions to all miners based on the trust value calculated by [Yuma Consensus](doc:consensus), while others may limit emissions. For example, Subnet 6 currently only distributes emissions to the top x miners:

<Image alt="Subnet 6 miner emissions - showing only top 6-10 miners receive any significant emission.  (Feb. 5, 2024)" align="center" src="https://files.readme.io/3dc6554-image.png">
  Subnet 6 miner emissions - showing only the top 6-10 miners receive any significant emission. (Feb. 5, 2024)
</Image>

Learning to read the [Subnet Metagraph table](doc:metagraph#miner-view) is a helpful step to better understand emission distribution.

See [Tao Allocation](doc:tao-allocation) for a mathematical description of how tao is allocated to miners.

# De-registration

The registration tab for each subnet lists the number of registrations in the last 24 hours. Assuming a full subnet - this is equal to the number of de-registrations.

[https://taostats.io/subnets/netuid-`<subnetID>`/#registration](https://taostats.io/subnets/netuid-13/#registration)

<Image align="center" width="26%" src="https://files.readme.io/76de496-image.png" />

The new miners will have immunity for a set period, so a large number of new registrations will push your miner closer to the bottom of the incentive list (by percentage). Each subnet has a different immunity period, which

If you know your miner's emission value, it is possible to mouse over the incentive chart to see where you stand:

![](https://files.readme.io/56c9763-image.png)

> 📘 Sort the metagraph by incentive (increasing) show 100 entries at a time.
>
> If your miner appears here, you are in the bottom 100 miners (note that all the validators also appear in this list)
>
> This view will also show miners with immunity, so depending on the competitiveness of the Subnet, miners on this view are very close to being de-registered.