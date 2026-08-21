---
title: Creating a miner
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

A miner deploys (at least) one mining node into (at least) one subnet to perform the work being rewarded by the subnet incentive mechanism. The object of a miner is to score higher than their peers and not fall into the bottom percentile and risk deregistration.  The longer a miner remains active, the more profitable they become. Miners may operate multiple nodes on multiple subnets.

The taostats [mining dashboard](https://taostats.io/pro/mining)  helps you track how well your miners are doing.

When mining, miners ensure that their servers are operating - accepting requests from validators and returning responses. Miners can modify their mining server and code to best meet the incentive mechanism for the subnet.

Mining is highly competitive - the "best" miners in each subnet accumulate more emissions, and the miners with the lowest scores are de-registered from the network.

The miner persona runs [Miner servers](/docs/mining) in a subnet. To mine, research all of the subnets (see the [Bittensor Subnets](/docs/list-of-subnets) list), and decide which subnet you wish to mine.  Each subnet has different hardware and software requirements.  Some subnets have a testnet to test your miner before registering and mining in the subnet.

You'll need to [register a node](/docs/node-registration) with a Bittensor hotkey.  Then you'll start your miner code on your server with the same hotkey to verify your server on the network.

# Ranking

Each miner participates in a subnet.  It solves the challenge specific to that subnet, and the miner's responses are evaluated by validators based on the subnet's criteria. The validators then weigh (or rank) the responses of all miners and rank them via weights. The weights are posted to [Yuma Consensus](/docs/consensus) to create an incentive score - and the higher the incentive, the higher the reward.

If a miner's server falls into the bottom of the miner trust rankings for a subnet, it risks being de-registered.

Reward for miners is scored as incentive that is converted to emission..

# Rewards

Miners receive alpha as an award for the work produced.  The reward is based on their ranking as scored by the specific subnet's incentive mechanism.

The emission scores for all miners sum to 1.  This is then used to allocate the emissions awarded to the miners.

The [Tokenomics](/docs/tokenomics) section describes how tao is distributed in the Bittensor ecosystem.

* Some subnets have "winner-takes-all" awarding (or a few winners-take-all).
* Incentive awarded to the Subnet owner is burned.

## Where do your awards go?

Miner alpha rewards will automatically stake to the hotkey.

If you would like your mining rewards to be automatically staked to a validator, this can be set via `Autostake`

### Autostake your rewards

With autostake, all incentive from all hotkeys are automatically staked to one hotkey. Generally, a miner would choose a validator to earn staking rewards.

This does complicate the separation of mining rewards with staking rewards. There is a Taostats API for the transfer of mining rewards:

# Helpful links

* [Taostats: For Miners](/docs/taostats-for-miners)
