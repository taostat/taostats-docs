---
title: Subnet Pools
excerpt: Last updated Feb 2
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Subnet pools are liquidity pools that are used to exchange tao for alpha tokens

# What is a Subnet Pool?

A subnet pool (AKA liquidity pool) is a way to exchange between two currencies. In the case of subnet pools, they are used to exchange tao into the subnet's alpha token.  There are two values in the subnet pool: `alpha_in` and `tao_in`

* **alpha_in**: The amount of alpha currently in the subnet pool
* **tao_in**: The amount to tao currently in the subnet pool.

Inside the pool, the tao/alpha ratio is a constant.  Another way to think about this is that the product of the two values is a constant k:

<Image align="center" border={false} width="50% " src="https://files.readme.io/1f998f12d0010bdc3c676a0b68da311153f8fa0bb345818a9e5c0669706bcf1c-image.png" />

<br />

> 📘 Example subnet pool (shown in yellow) with 100τ and 100α.
>
> <Image border={false} src="https://files.readme.io/d0b38dd0a67438244876ee502dfd6c319f88921f19ce48151752dbd218e212b1-image.png" />
>
> k = 100* 100 = 10,000

<br />

## Emissions

Each block, tao and alpha are emitted into the liquidity pool.

* [Tao emission](https://docs.taostats.io/v2.0/docs/tao#distribution-of-emitted-tao)
* [Alpha Emission](doc:alpha-emission)

Note that the value of k with change with each block as a result of this emission.

## Alpha Price

The subnet pool determines the alpha price (shown in tao).

<Image align="center" border={false} width="50% " src="https://files.readme.io/d8bf29448d71b415d59c472a882819ef507178fbc4c005550ba647dd33f25e76-image.png" />

> 📘 If there is 100 tao_in, and 100 alpha_in, the α_price will be 1 tao.

## Subnet Pool Initialization

When a new subnet is registered, how much tao is placed into the pool?

* `initial_tao = 1`
* `initial_alpha = 1`

The initial `alpha_price` is 1.
