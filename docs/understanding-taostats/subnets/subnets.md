---
title: Infoboxes
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

The [Subnets page](https://taostats.io/subnets)  is the entryway into the world of subnets.  At the top of the page are three infoboxes with an overview:

## Subnets Value

This shows the sum of subnet prices (in tao).  Root always has a price of 1.  In the chart below, the sum of subnet prices is 1.60.

<Image border={false} alt="Taostats subnets value widget showing total value in TAO with a root/alpha proportional split bar" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/428b4f1c7c661a14.png" />

## Stake Split

The division of stake between root and subnets.

<Image border={false} alt="Taostats total stake split widget showing total stake in TAO with a root/alpha proportional split bar" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/471bc81655dc2085.png" />

## Total Volume

Total buys and sells on root vs. total buys and sells on other subnets.

<Image border={false} alt="Taostats total volume widget showing 24-hour volume in TAO with a root/alpha proportional split bar and paired values" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/611b67b5800c1c12.png" />

The initial sort is by Market Cap.

Subnet data can be shown in tao values (where all alpha token is converted into tao) or in USD.

<Image border={false} alt="Taostats subnets ranking table with rank, subnet, emission, price, 1H/24H/1W change, market cap, volume, liquidity, and 7-day sparkline columns above a TAO/USD toggle" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/658151ca33c115f9.png" />

* *Name*\*: The name and netuid of the subnet.
* **Emission**: The subnet's share of per-block TAO emission. As of 2026-06-30, determined by `subnet-price EMA × (1 − miner_burned)`, renormalized (subtensor PR [#2800](https://github.com/opentensor/subtensor/pull/2800) removed the earlier `root_proportion` weighting). See [Price-based subnet emission shares](/docs/price-based-emission-shares).
* **Price**: The [Alpha Price](/docs/#alpha-price)  of the subnet.
* **1H**: Price trend over the previous hour.
* **24H**: Price trend over the previous day.
* **1W**: Price trend over the previous week.
* **1M**: Price trend over the previous month.
* **Market Cap**: The Circulating supply of alpha token (this can be displayed in tao or in USD.)
* **Volume**: Amount traded in the last 24 hours (in tao or USD.)
* **Liquidity**: Total value of tokens in the [Subnet Pool](/docs/subnet-pools).
* **V3**: Are V3 liquidity options available?
* **Liq Price**: The liquidation price for the subnet — the effective per-alpha TAO holders would receive if the subnet's pool were drained today. Compare to the current price: if liq price is *above* current, holders would be paid a premium versus market; if *below*, they would take a loss. (Replaces the old ADR metric.)
* **Root Prop**: Percentage of validator emissions to root.
* **Root Sell**: Deprecated.

# Subnets Total Price

A chart showing the sum of subnet prices over time.

<Image border={false} alt="Taostats subnets total price combo chart overlaying a price area line with volume bars against price and volume axes over time" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/00a18b119eaca057.png" />

# Subnet Top Emissions

<Image border={false} alt="Taostats subnet top emissions multi-line time-series chart of top subnets' emission share with color-coded legend cards and a percentage axis" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/1db0fdc1e7d34241.png" />

# Subnet Registration Cost

Cost in tao to register a new Subnet. 1 tao from registration cost is added to the Subnet pool. The remainder is recycled.

<Image border={false} alt="Taostats subnet registration cost area chart plotting the TAO cost to register a new subnet over time with a current-cost stat" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/3fe75f9258b9558d.png" />

# Subnet Deregistration List

When a new subnet is registered, the subnet with the lowest EMA price is deregistered.

<Image border={false} alt="Taostats subnets deregistration list table with subnet, pruning rank, EMA, remaining immunity, and immune-status columns plus an immune-hide filter" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/584cfccafe20b048.png" />
