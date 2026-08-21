---
title: Getting started: the data
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

When looking at your miner's activity in taostats - there are probably a few different ways you want to interact:

1. [The metagraph](/docs/#the-metagraph-for-miners) to see how your miner(s) are doing in relation to the other neurons.
2. [Coldkey view](/docs/coldkey-view): A view of all your miners in one place.
3. [Hotkey view](/docs/hotkey-page): A detailed view of a specific miner.

# The metagraph: for miners

Each subnet publishes a Metagraph - a giant table of data about each node. See [Subnet Metagraph table](/docs/#miner-view) for details on how to best sort the metagraph, and how to read the data.

The columns most relevant to miners are *trust*, *incentive* and *emission*.

* Trust: Scored by validators on how "trustworthy" your results are. What this means varies from Subnet to Subnet.
* Incentive: The percentage of miner emission that will be awarded to each miner. The sum of this column is 1.
* Emission: This is the tao awarded each epoch. This is calculated from the incentive and the miner's share of emissions. Note that Emission is shown *per epoch*, or 360 blocks.
* Daily tao: Emission \*20 (\~ 20 epochs per day). Note: This is an instantaneous calculation - not a predictor.
* Daily$: is daily tao \* current price of tao. Note: This is an instantaneous calculation - not a predictor.

<Image border={false} alt="Taostats subnet metagraph table with POS, UID, stake, trust, consensus, incentive, dividends, emission, axon, hotkey, coldkey, and daily reward columns" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/5f3ead0d6c866c9f.png" />

# ColdKey View

The [Coldkey view](/docs/coldkey-view) in taostats will show details about a specific coldkey wallet, including details about any active hotkeys. `https://taostats.io/coldkey/&lt;your coldkey&gt;` to see your miner's data.

<Image border={false} alt="Taostats coldkey view page with summary cards for neurons, hotkeys, rewards, and stake above a subnet-grouped metagraph table" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/7a3ce1c7f94a7898.png" />

# Registering a node

To mine, you need to know how competitive a subnet is, how much it costs to register a node on the subnet, and how the subnet distributes emissions to miners. Register a node using the [Command Line Tool](/docs/command-line-tool)"

```
btcli subnet register
```

## Subnet emissions

Each subnet is granted a percentage of the blockchain [emission](/docs/subnet-emissions). High-emission subnets are more profitable, but also more competitive. Miners receive 41% of the emission for the subnet. The emission for each subnet can be found in multiple places in taostats:

* Subnet pages

  <Image border={false} alt="Taostats subnet header on an older layout showing identity metadata and a stat strip of emissions, recycled, registration cost, and key counts" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/7630b2bef832f856.jpg" />
* [https://x.taostats.io/subnets](https://x.taostats.io/subnets)

<Image border={false} alt="Taostats subnet top emissions view on an older layout with color-coded subnet legend cards above a multi-line emission-share time-series chart" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/f1b91fde492853e3.jpg" />

<Image border={false} alt="Taostats subnets list on an older layout, a sortable table with ID, name, registration date, owner, emission, recycled, and lifetime columns" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/9c4e686f8a0458e0.jpg" />

* [taostats.io](taostats.io) homepage:

<Image border={false} alt="Taostats root metagraph table on an older layout with rank, UID, hotkey, TAO staked, and per-subnet percentage columns" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/8cb156bd9e684837.jpg" />

## Miner Incentive distribution

Subnets with higher emissions tend to be more competitive for miners, meaning that the risk of being deregistered is high. The competitiveness of a subnet can be seen on subnet[individual subnets distribution graphs](https://taostats.io/subnets/netuid-19/#distribution). For example:

<Image border={false} alt="Snapshot of Subnet 13" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/e8af0ab67b8500ad.jpg" />

<Image border={false} alt="Snapshot of subnet 19" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/6ac84138698968b5.jpg" />

In the first screenshot, there is a large distribution of emissions. In this subnet, a well-performing miner can keep above the threshold for de-registration.

In the second screenshot, the range for Active keys is very narrow (0.00401 - 0.00441). Any minor disruption to your miner may cause you to fall to the bottom of the emissions chart and be deregistered.

## Node Registration cost

You can view the current registration cost at [https://taostats.io/subnets/netuid-\<subnetID>/#registration](https://taostats.io/subnets/netuid-19/#registration). Competitive subnets generally cost more to register a node than non-competitive nodes.

### Deregistration

<Image border={false} alt="Taostats subnet deregistration data dual-axis time-series chart plotting incentive and emission of recently deregistered miners over time, with summary stat pills" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/f82f51f7edbf9eec.jpg" />

When a new miner is registered, the lowest miner out of immunity is deregistered. Any new miner should aim to be above the last deregistration incentive before they exit immunity.

## Immunity period

Each new node is granted immunity for a defined number of blocks. When you have immunity, you cannot be de-registered. The [Node Registration](https://taostats.readme.io/docs/node-registration) page describes how to use the BTCLI to determine a subnet's immunity period.

## Emission Distribution

Some subnets evenly distribute emissions to all miners based on the trust value calculated by [Yuma Consensus](/docs/consensus), while others may limit emissions. For example, Subnet 6 currently only distributes emissions to the top x miners:

<Image border={false} alt="Subnet 6 miner emissions - showing only top 6-10 miners receive any significant emission. (Feb. 5, 2024)" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/421eb2f67aca6661.png" />

Learning to read the [Subnet Metagraph table](/docs/#miner-view) is a helpful step to better understand emission distribution.

See [Subnet emission overview](/docs/split-alpha-out) for a description of how tao is allocated to miners.

# De-registration

The registration tab for each subnet lists the number of registrations in the last 24 hours. Assuming a full subnet - this is equal to the number of de-registrations.

[https://taostats.io/subnets/netuid-\<subnetID>/#registration](https://taostats.io/subnets/netuid-13/#registration)

<Image border={false} alt="Taostats subnet registrations table with UID and hotkey columns plus a 24-hour registration count stat and rows-per-page selector" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/af8bbae349f87b03.png" />

The new miners will have immunity for a set period, so a large number of new registrations will push your miner closer to the bottom of the incentive list (by percentage). Each subnet has a different immunity period, which

If you know your miner's emission value, it is possible to mouse over the incentive chart to see where you stand:

<Image border={false} alt="Taostats miner incentive scatter chart across UIDs with a hover tooltip showing UID, incentive, rank, registration block, keys, and immunity status" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/5f0db7fd3fde40f1.jpg" />

> 📘 **Sort the metagraph by incentive (increasing) show 100 entries at a time.**
>
> If your miner appears here, you are in the bottom 100 miners (note that all the validators also appear in this list)
>
> This view will also show miners with immunity, so depending on the competitiveness of the Subnet, miners on this view are very close to being de-registered.
