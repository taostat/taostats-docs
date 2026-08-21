---
title: Staking
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

Understand how to read the data in order to stake your tao

Staking is a great option if you want to support the Bittensor network with tao, but do not want to run a subnet or neuron.

> 📘 [**Staking Instructions**](/docs/staking-instructions) — Use taostats for all your staking transactions!

Staking is the process of delegating your tao to a validator.

## Root stake

Validators with high VTrust across as many subnets as possible will have the highest root returns.  You can also choose to support validators who work towards building the Bittensor ecosystem (with higher emissions, validators earn more tao, so by supporting validators who work on the ecosystem, you support their work.)

## Alpha Stake

Staking in a subnet involves buying an alpha token.  See [Staking in dTao](/docs/staking-in-dtao) for full details. Your alpha quantity grows over time through autocompounding, but the exchange rate between tao/alpha can change — so the tao value of your stake can still fall, leading to a net loss of funds.

Because alpha staking trades through a subnet pool, it can be targeted by MEV bots. Alpha stake/unstake transactions on Taostats are protected by [MEV Shield](/docs/mev-shield) — and Taostats **signs the encryption wrapper for you**, so there is no second signature to enter.

## Staking hold period

There is no hold period for staking.

## Staking Risk

* **Root**: Staking on root Bittensor is the lower-risk option. Your tao is delegated to a validator's hotkey — the validator can set weights with it but cannot withdraw or transfer it, and you can unstake at any time. Returns still depend on the validator's performance and on root's declining share of total emissions.
* **Alpha**: When buying alpha, you are purchasing a new token. Your alpha quantity grows through autocompounding, but the price of alpha/tao will fluctuate — so the tao value of your position can fall. This can lead to a loss in funds.

## Choosing a validator

Learn about the validators, and how they are contributing to the Bittensor network. By staking with a validator, you are supporting this work.  The table shows the amount of tao that is delegated to them, and the % of network delegated tao:

<Image border={false} alt="Taostats validator as of Feb. 5 2024." src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/f1063f59a1f9c0ee.jpg" />

The info button takes you to the [validator explorer](/docs/#explorer)  page, providing details about the validator's performance.

## Return on your stake

When you stake your TAO on a validator, you'll want an idea of the amount of emissions you will receive. Taostats has a *very basic* calculator that uses the average emissions across the entire bittensor network: [https://taostats.io/staking/](https://taostats.io/staking/).

<Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=GzB381fBQQM" href="https://www.youtube.com/watch?v=GzB381fBQQM" providerUrl="https://www.youtube.com/" providerName="YouTube" />

# APY

[https://taostats.io/yield](https://taostats.io/yield) displays the APY for all subnets including root

<Image border={false} alt="Dark-themed validator yield table with subnet selector, simulation input, and validator, stake, and 1H/1D/1W/1M APY columns as colored pills" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/01e1461968f25d32.png" />

This page is calculated based on **actual returns** over the period.  As always *past performance does not indicate future gains*.

Root APY will be in decline as subnets mature, due to [Emissions: Root vs. Alpha Stake](/docs/stakeholder-emissions-root-vs-alpha).
