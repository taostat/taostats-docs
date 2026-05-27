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

The values shown below assume that alpha has not halved, and one full alpha can be emitted each block to alpha_in and alpha_out. At the alpha halvening, the alpha emitted will drop by a factor of 2.

## alpha_in

To find the amount of alpha added to the subnet pool, find the tao emitted into the pool, and divide by the price of the alpha.

This keeps the ratio of alpha and tao values in the pool equal.

![](https://files.readme.io/eecaa0d5d796c501766c848a87deceb21094cb61fd6ae5119f14bffbbb684b7d-image.png)

> 📘 Note: the max value for alpha_in is 1.
>
> if the calculation above would result in alpha_in >1, then the tao_in is reduced to the value that makes alpha_in 1.
>
> The difference in tao_in is sold through the [Subnet Pools](doc:subnet-pools) and the alpha received is [Recyled](doc:recycling).

<br />

## alpha_out

The alpha emitted to subnet participants is 1 alpha per block (until an alpha halvening).  To learn how this is distributed, see [Subnet Emission](doc:subnets-1).  
