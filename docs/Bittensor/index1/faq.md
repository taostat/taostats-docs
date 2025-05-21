---
title: FAQ
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
# General

## What is the Metagraph?

The metagraph is a tabular output of the data metrics associated to all subnets participants at any given moment in time.  It can be accessed via the `btcli s metagraph`, but for easy sorting and organisation of the data, [taostats](https://taostats.io) displays this data for the community with some additionally calculated fields that are not in the CLI version.

# Staking/Delegation

## I have some tao. Which validator should I delegate it to?

Awesome - welcome to Bittensor.  The [Taostats: For Staking](doc:taostats-for-staking) page has detailed information to help you decide which validator to stake with. There is no hold period for staking/unstaking.

## Is staking/delegation safe? Will the validator take my tao?

Your tao remains in a hotkey under your control.  The validator has no access to your tao, and you may unstake at any time (rate limits do apply - the current hotkey stake/unstake rate limit is 1x per 360 blocks).

# Mining

## How do I get started?

Here are some general ideas on how to get started mining. [Taostats: For Miners](doc:taostats-for-miners) describes important data characteristics you will want to track.

1. Mining is Subnet specific: You will want to learn about the [Subnets](doc:list-of-subnets), 
2. Read the mining requirements for your subnet. Each github repository should have details with the hardware and software requirements.
3. Note the current and historical costs of registering a node on the subnet.
4. Start on a testnet (if possible);
5. [Register for a neuron](doc:node-registraion) on mainnet.

## Why did I get de-registered?

Mining in Bittensor is competitive - there are a limited number of slots available to mine on each subnet.  If your miner falls to the bottom of the emission column in the metagraph of your subnet, it will be de-registered when a new neuron is registered. [Taostats: For Miners](doc:taostats-for-miners) shows how to read the metagraph to gauge the rank of your miner.

# Tao

## How do I buy tao?

The [Tao Community exchange channel](https://discord.com/channels/1086368192521318472/1180148763067699241) has an updated list of exchanges.  The [wallet channel](https://discord.com/channels/1086368192521318472/1177226246048972820) contains information on wallets that support tao.

## How is tao distributed?

[Yuma Consensus](doc:consensus) is the consensus model used to distribute tao emissions. See the [Tao Allocation](doc:tao-allocation) page for a description of the emission and distribution mechanism.

# Security

## Is the data I send to a Bittensor secure? Can I send private information to a subnet?

Any data transmitted to Bittensor will pass through multiple servers, including a validator and a miner. There is no guarantee of data security, and you should use extreme caution in transmitting private or confidential information through the Bittensor network.

<br />

# Hotkey/Coldkey What's the difference?

In Bittensor, your coldkey is your wallet. One coldkey can have many hotkeys.  Your coldkey is used to transfer and hold tao.  Hotkeys are used on the chain to register neurons (miners & validators), and stake tao on validators.  Tao that is earned on the hotkey is staked to the hotkey.  Upon de-registration or de-staking, the tao is transferred to the wallet's coldkey.
