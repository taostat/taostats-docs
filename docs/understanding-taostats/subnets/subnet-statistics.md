---
title: Subnet Price and Volume
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

<Image border={false} alt="Taostats subnet price and volume chart combining a price area line with volume bars, a TAO/USD toggle, and a time-range selector" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/d9f7f7e3e1098b31.png" />

# Subnet Emission

The subnet's share of per-block TAO emission. As of 2026-06-30, determined by `subnet-price EMA × (1 − miner_burned)`, renormalized across subnets (subtensor PR [#2800](https://github.com/opentensor/subtensor/pull/2800) removed the earlier `root_proportion` weighting). See [Price-based subnet emission shares](/docs/price-based-emission-shares).

<Image border={false} alt="Taostats subnet emission area chart plotting the subnet's emission share percentage over time with a time-range selector" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/fdf26cad5fb5fb85.png" />

# Subnet Root Proportion

<Image border={false} alt="Taostats subnet root proportion dual-line time-series chart plotting root versus alpha percentage split over time" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/938bfca643d3e142.png" />
