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
# Accounts

## Why was there a big drop in accounts in May 2024?

<Image align="center" width="50%" src="https://files.readme.io/d5fedce-image.png" />

Due to a chain upgrade, all accounts had to be migrated, but this migration had impacts to the chain. To mitigate this impact, empty accounts were not migrated. [twitter thread](https://x.com/taostats/status/1794719922486223324)

# General

## What is the Metagraph?

The metagraph is a tabular output of the data metrics associated to all subnets participants at any given moment in time. It can be accessed via the `btcli s metagraph`, but for easy sorting and organisation of the data, [taostats](https://taostats.io) displays this data for the community with some additionally calculated fields that are not in the CLI version.

# Staking/Delegation

## I don't see my staking rewards!

Go to taostats.io/account/&lt;coldkey&gt;. Mouse over the chart, and you'll see the staking number increase over time. Staking reward are added to your wallet once every 7200 blocks (approx. 24 hours). You may not see your frist reward for 36-48 hours.

## I have some tao. Which validator should I delegate it to?

Awesome - welcome to Bittensor. The [Taostats: For Staking](doc:taostats-for-staking) page has detailed information to help you decide which validator to stake with. There is no hold period for staking/unstaking. If you are looking for a suggestion, we like taostats and Corcel.

## Is staking/delegation safe? Will the validator take my tao?

Your tao remains in a hotkey under your control. The validator has no access to your tao, and you may unstake at any time (rate limits do apply - the current hotkey stake/unstake rate limit is 1x per 360 blocks).

## Is the [Taostats delegation](https://delegate.taostats.io/) tool safe? Will Taostats have my wallet credentials?

It is safe. All staking is done on chain, and taostats does not get your seed phrase or wallet credentials.

## Why does Staking APY decrease over time?

The short answer is that the math guarantees it. See [this link](https://docs.taostats.io/v1.1/docs/calculator#why-is-the-staking-apr-declining) for the details.

# Mining

## How do I get started?

[Starting as a Miner](doc:i-want-to-mine-on-bittensor): Grew into its own page.

## Why did I get de-registered?

Mining in Bittensor is competitive - there are a limited number of slots available to mine on each subnet. If your miner falls to the bottom of the emission column in the metagraph of your subnet, it will be de-registered when a new neuron is registered. [Taostats: For Miners](doc:taostats-for-miners) shows how to read the metagraph to gauge the rank of your miner.

## My miner has zero emissions? is this a bug?

It is important to do you own research before registering on a subnet to understand how emission is granted to miners. Mining is extremely competitive, and using the base miner is often "not enough" to receive emissions. Additionally, each subnet awards emission differently. Some Subnets only award emission to the top "x" miners. In others, the time to receive emission varies - but in general you'll need at least one epoch for the validators to grade you and set weights.

If the Subnet has no emissions:

![](https://files.readme.io/2c37bf4-image.png)

# Tao

## How do I buy tao?

The [Tao Community exchange channel](https://discord.com/channels/1086368192521318472/1180148763067699241) has an updated list of exchanges. The [wallet channel](https://discord.com/channels/1086368192521318472/1177226246048972820) contains information on wallets that support tao.

## How is tao distributed?

[Yuma Consensus](doc:consensus) is the consensus model used to distribute tao emissions. See the [Tao Allocation](doc:tao-allocation) page for a description of the emission and distribution mechanism.

# Security

## Is the data I send to a Bittensor secure? Can I send private information to a subnet?

Any data transmitted to Bittensor will pass through multiple servers, including a validator and a miner. There is no guarantee of data security, and you should use extreme caution in transmitting private or confidential information through the Bittensor network.

## There was a hack in July 2024. What happened?

From July 2-12, 2024, the chain was placed into safe mode - preventing transactions from being performed. In the minutes before the chain was placed in safe mode, several large accounts were drained of tao.

The origins of the attack stem from the release of Bittensor 6.12.2 in May 2024. The pip version of this release had a compromised library that allowed the hacker to collect unencrypted coldkeys. On July 2, 2024, the attacker used these credentials to empty several wallets. *ONLY* users of the command like tool BTCLI - version 6.12.2 - were compromised. [Blog post](https://blog.bittensor.com/bittnesor-community-update-july-3-2024-45661b1d542d) describing the attack, and the [process to reopen the chain](https://blog.bittensor.com/reopening-bittensor-8252ee749980). During the reopening and coldkey swap - no further wallets were attacked.
Our [A Best Practices Guide for Safely Installing Software](doc:a-best-practices-guide-for-safely-installing-software) provides a template for ensuring you are operating as safely as possible when installing dependencies.

# Hotkey/Coldkey What's the difference?

In Bittensor, your coldkey is your wallet. One coldkey can have many hotkeys. Your coldkey is used to transfer and hold tao. Hotkeys are used on the chain to register neurons (miners & validators), and stake tao on validators. Tao that is earned on the hotkey is staked to the hotkey. Upon de-registration or de-staking, the tao is transferred to the wallet's coldkey. [Coldkey/Wallets](ref:coldkeywallets) section has more information.