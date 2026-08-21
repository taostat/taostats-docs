---
title: Subnet pages
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

Selecting a subnet from the Subnet dropdown will load detailed information about the subnet.

In the upper left, find a description and links to external sites for the subnet. (A Github link is shown in the screenshot.)

<Image border={false} alt="Taostats subnet detail page with a left identity panel, description, external links, price panel, and financial stats beside a right tabbed candlestick chart" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/65f63d2c60f267e9.png" />

* [Price](#price)
* [Financial Data](#financial-data)
* [Staking Data](#staking-data)
* [Staking: Taostats Subnet page](/docs/staking-taostats-subnet-page)
* [Subnet Data](#subnet-data)
* [Subnet Trading View Chart](/docs/subnet-trading-view-chart)
* [Metagraph](/docs/metagraph)
* [Subnet parameters](/docs/subnet-parameters)
* [Subnet Registration Charts](/docs/registration)
* [Distribution](/docs/distribution)
* [Miner Weights](/docs/miner-weights)
* Emission
* [Sentiment](/docs/sentiment)

## Price

The price of the alpha token in both tao and USD. [Alpha Tokens](/docs/alpha-tokens) describes the math to find the price.

<Image border={false} alt="Taostats subnet price panel showing the alpha token price in TAO and USD with a percent-change badge and sparkline" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/db0f7ee79a4437eb.png" />

## Financial Data

<Image border={false} alt="Taostats subnet financial data panel, a grid of stat cards for market cap, volume, FDV, supply, and pool figures with a pool ratio bar" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/1eece2d1f8c168a7.png" />

* **Market Cap**: The value of the subnet alpha in USD.
* **Volume**: tao/alpha traded in the last 24 hours (in USD).
* **FDV**: Fully Diluted Value: Price \* Max Supply (which is 21M tokens)
* **Vol/Market Cap/24hr**: Percentage of market cap traded in the last day.
* **Max Supply**: Max number of tokens.
* **Circulating Supply**: Total amount of alpha in circulation.
* **Alpha in Pool** : The amount of alpha in the Subnet liquidity pool.
* **Tao in Pool** : The amount of tao in the Subnet liquidity pool.

## Staking Data

A summary of all staking/unstaking events in the previous 24 hours.

<Image border={false} alt="Taostats subnet trading data panel with paired buy/sell metrics for orders, volume, and participants, each shown with a green/red ratio bar" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/8cc2b7100bcaf6e2.png" />

## Sentiment

An algorithm to sense buy/sell sentiment of investors on the subnet.

[Sentiment](/docs/sentiment)

## Subnet Data

<Image border={false} alt="Taostats subnet data panel, a grid of stat cards for emissions, per-day emission splits, registration cost, recycled, and UID counts" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/3eed9db5dd006de1.png" />

* **Emission**: The % of tao emitted into the Subnet pool.  If 1 tao is emitted per block, emission/100 is the amount of tao emitted into the pool.
* **Root Proportion**: The percentage of stakeholder returns that are split to root stakeholders vs. alpha stakeholders.
* **Emission/Day**: Tao injected by the chain into the SN pool per day.
* **Owner/day**: 18% of the tao injected.
* **Miner/day** 41% of the tao injected.
* **Validator/day** 41% of the tao injected.
* **Registration cost** Cost to register a neuron.
* **Recycled/day**: tao recycled for neuron registration. This is the sum of the fees paid for miner and validator registrations.
