---
title: Tao Summary
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

The landing page of Taostats provides a high level overview of several important aspects of the Bittensor network.

* [Tao Summary](#tao-summary)
* [Tao Trading Chart](#tao-trading-chart)
* [Subnet overview](#subnet-overview)
* [Subnet 0 data](#subnet-0-data)

Across the top of the homepage is a summary of the current trading state of the $TAO token.

<Image border={false} alt="Taostats homepage Tao Summary showing $TAO price, market cap, 24h volume, supply, blocks, accounts, and transfer counts" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/995c683b1bdf09da.png" />

* **Current price**: in USD (and daily change)
* **Market cap**: the value of all the **τ**  currently in circulation.
* **24h Volume**: How much **τ** was traded in the last day.
* **Circulating Supply**: **τ** that has been minted and can be traded.
* **Total Supply**: In \~2045, the final **τ** will be created, and there will be 21M TAO in circulation.

# Tao trading chart

This chart lists the historical price and trading volume of **τ**.

* The price of **τ** is shown with an orange line.
* The daily volume is a blue bar chart, where each bar is one day's trading (in millions of USD).

**Chart controls:**

* **Trading View**: toggles on/off a trading view version of the chart
* **Plus and minus buttons:** zoom in and zoom out.
* **Magnifying glass**   select the zoom region

You can also click and zoom with a mouse.

<Image border={false} alt="Taostats homepage TAO price line chart with volume bars spanning several years, with a hover tooltip showing price and volume for a selected date" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/edec90313287c15c.png" />

# Subnets overview

This summary of subnet data shows the top 8 subnets based on emission:

* **Price**: The price of the alpha token, in tao.
* **Market Cap**: Price \* circulating supply of alpha
* **Emission** : percentage of tao that is emitted into the pool. [Subnet Emission](/docs/subnet-emissions)is determined by the price of the token.
* **Last 7 days** Price over the last 7 days.

<Image border={false} alt="Taostats homepage Subnets overview table listing subnet name, ID, price, market cap, emission percentage, and a 7-day sparkline, sorted by emission" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/f3c49c0628b77fae.png" />

# Validator Overview

A summary of the top 8 validators (based on weighted stake).

* **Weight**: root stake \*18% + sum of all alpha stake (in tao)
* **Weight Change**: delta over the last day.
* **Nominators**: Sum of nominators across all subnets.
* **Root:Alpha**: Breakdown of Weight into root & Alpha contributions.

<Image border={false} alt="Taostats homepage Validators overview table with validator name, weight, 24h weight change, nominator count, and a Root:Alpha percentage split bar" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/0929adf26ed21677.png" />

# Transfers:

A live view of all purchase activity with tao:

<Image border={false} alt="Taostats homepage live Transfers table showing From, To, TAO amount, extrinsic ID, and time for recent transfers including Binance and Kraken Hot" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/511d83cb7e4f0000.png" />

# Blocks

A live block explorer:

<Image border={false} alt="Taostats homepage live Blocks explorer table listing block height, spec version, hash, event count, extrinsic count, and time for recent blocks" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/834df781b80816af.png" />

# Transactions

Live listing of staking transactions

<Image border={false} alt="Taostats homepage live Transactions table of subnet staking buys and sells with time, action, subnet, delegate, alpha, TAO, price, and coldkey columns" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/bead2d97dd4dd28e.png" />
