---
title: Alpha Emission
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
Every block, up to two alpha are emitted into each subnet. This is split between the subnet pool `alpha_in` and the `alpha_out` (the emissions rewarded to the subnet owner, miners and validators and stakeholders)

# Calculations

## alpha\_in

To find the amount of alpha added to the subnet pool, find the tao emitted into the pool, and divide by the price of the alpha.

This keeps the ratio of alpha and tao values in the pool equal.

![](https://files.readme.io/eecaa0d5d796c501766c848a87deceb21094cb61fd6ae5119f14bffbbb684b7d-image.png)

> 📘 Note: the max value for alpha\_in is 1.

<br />

## alpha\_out

The alpha emitted to subnet participants is 1 alpha per block.  To learn how this is distributed, see [Subnet Emission](doc:subnets-1).