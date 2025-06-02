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

<br />

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

![](https://files.readme.io/1cae8e2f93e0061c70ee491141171d2c9a3b5aa2576a2fb79af170a515761fd0-image.png)

<br />

# ColdKey View

The [Coldkey view](doc:coldkey-view) in taostats will show details about a specific coldkey wallet, including details about any active hotkeys. `https://taostats.io/coldkey/&lt;your coldkey&gt;` to see your miner's data.

![](https://files.readme.io/9178dce1630713489fa20ea313bb0ddf66124c0bf6d7b1bdaadc9e204728366a-image.png)

<br />

# Registering a node

To mine, you need to know how competitive a subnet is, how much it costs to register a node on the subnet, and how the subnet distributes emissions to miners. Register a node using the [Command Line Tool](doc:command-line-tool)"

```
btcli subnet register
```

## Subnet emissions

Each subnet is granted a percentage of the blockchain [emission](doc:subnets-emission). High-emission subnets are more profitable, but also more competitive. Miners receive 41% of the emission for the subnet. The emission for each subnet can be found in multiple places in taostats:

* Subnet pages

  <Image align="center" src="https://files.readme.io/c53bc8b63c48e0eef2b55fd06cf3296c744869490face61fb5b014c6b9460e38-Screenshot_2024-09-06_at_13.45.07.jpg" />
* [https://x.taostats.io/subnets](https://x.taostats.io/subnets)

<Image align="center" src="https://files.readme.io/d08c4f14bccc06f12e9e35b21bd2c129750f3382f7f15a7655d323a9ce109292-Screenshot_2024-09-06_at_13.45.55.jpg" />

<Image align="center" src="https://files.readme.io/8c5737d38395f522e16e5cc3c23c62e6e5849b2f4a90a2fd61c2fafc9bb186fd-Screenshot_2024-09-06_at_13.46.32.jpg" />

<br />

* [taostats.io](taostats.io) homepage:

<Image align="center" src="https://files.readme.io/dfaa58705c8373756c74b3d172340d888de0c469b941a0b8e0bdb4206757bdb6-Screenshot_2024-09-06_at_13.47.17.jpg" />

<br />

## Miner Incentive distribution

Subnets with higher emissions tend to be more competitive for miners, meaning that the risk of being deregistered is high. The competitiveness of a subnet can be seen on subnet[individual subnets distribution graphs](https://taostats.io/subnets/netuid-19/#distribution). For example:

<Image alt="Snapshot of Subnet 13" align="center" src="https://files.readme.io/4805237b06bb1f3b7ea18849f3b5f29e2f6f33cbd752f1a836777fd8d40ad398-Screenshot_2024-09-06_at_13.56.56.jpg">
  Subnet with a wide distribution
</Image>

<Image alt="Snapshot of subnet 19" align="center" src="https://files.readme.io/daa6b371ebe7ba86eda6f53c6e2be5324cc57fc24a12f29ac371c2f8c84a0b03-Screenshot_2024-09-06_at_13.47.59.jpg">
  subnet with a narrow distribution
</Image>

In the first screenshot, there is a large distribution of emissions. In this subnet, a well-performing miner can keep above the threshold for de-registration.

In the second screenshot, the range for Active keys is very narrow (0.00401 - 0.00441). Any minor disruption to your miner may cause you to fall to the bottom of the emissions chart and be deregistered.

## Node Registration cost

You can view the current registration cost at [https://taostats.io/subnets/netuid-&lt;subnetID&gt;/#registration](https://taostats.io/subnets/netuid-19/#registration). Competitive subnets generally cost more to register a node than non-competitive nodes.

### Deregistration

<Image align="center" src="https://files.readme.io/3a11d7f8f5c1a52794ab1f2bc62eb57194628a3ec863e24bfd756282ccb3b755-Screenshot_2024-09-06_at_13.57.30.jpg" />

<br />

When a new miner is registered, the lowest miner out of immunity is deregistered. Any new miner should aim to be above the last deregistration incentive before they exit immunity.

<br />

## Immunity period

Each new node is granted immunity for a defined number of blocks. When you have immunity, you cannot be de-registered. The [Node Registration](https://taostats.readme.io/docs/node-registration) page describes how to use the BTCLI to determine a subnet's immunity period.

## Emission Distribution

Some subnets evenly distribute emissions to all miners based on the trust value calculated by [Yuma Consensus](doc:consensus), while others may limit emissions. For example, Subnet 6 currently only distributes emissions to the top x miners:

<Image alt="Subnet 6 miner emissions - showing only top 6-10 miners receive any significant emission. (Feb. 5, 2024)" align="center" src="https://files.readme.io/3dc6554-image.png">
  Subnet 6 miner emissions - showing only the top 6-10 miners receive any significant emission. (Feb. 5, 2024)
</Image>

Learning to read the [Subnet Metagraph table](doc:metagraph#miner-view) is a helpful step to better understand emission distribution.

See [Tao Allocation](doc:tao-allocation) for a mathematical description of how tao is allocated to miners.

# De-registration

The registration tab for each subnet lists the number of registrations in the last 24 hours. Assuming a full subnet - this is equal to the number of de-registrations.

[https://taostats.io/subnets/netuid-&lt;subnetID&gt;/#registration](https://taostats.io/subnets/netuid-13/#registration)

<Image align="center" width="26% " src="https://files.readme.io/76de496-image.png" />

The new miners will have immunity for a set period, so a large number of new registrations will push your miner closer to the bottom of the incentive list (by percentage). Each subnet has a different immunity period, which

If you know your miner's emission value, it is possible to mouse over the incentive chart to see where you stand:

<Image align="center" src="https://files.readme.io/be804fc832c9080660418a0f370a7ba6b99b4fb4b120570b1643f74b34c43676-Screenshot_2024-09-06_at_14.52.25.jpg" />

> 📘 Sort the metagraph by incentive (increasing) show 100 entries at a time.
>
> If your miner appears here, you are in the bottom 100 miners (note that all the validators also appear in this list)
>
> This view will also show miners with immunity, so depending on the competitiveness of the Subnet, miners on this view are very close to being de-registered.