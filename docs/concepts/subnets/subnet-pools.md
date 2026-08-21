---
title: What is a Subnet Liquidity Pool?
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

Subnet pools are liquidity pools that are used to exchange tao for alpha tokens

A subnet pool (AKA liquidity pool) is a way to exchange between two currencies. In the case of subnet pools, they are used to exchange tao into the subnet's alpha token.  There are two values in the subnet pool: `alpha_in` and `tao_in`

* **alpha\_in**: The amount of alpha currently in the subnet pool
* **tao\_in**: The amount to tao currently in the subnet pool.

Inside the pool, the tao/alpha ratio sets the price.  In the simplest case the pool behaves like a constant-product AMM — the product of the two reserves is a constant k:

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/9d5e799bc7328ce0.png" />

> 📘 **Example subnet pool (shown in yellow) with 100τ and 100α.**
>
> <Image border={false} alt="Diagram of a two-sided subnet pool with a tau reserve container and an alpha reserve container meeting at a highlighted pooled-reserve region" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/d30b1ff53b9bf1c3.png" />
>
> k = 100\* 100 = 10,000

## Emissions

Each block, tao and alpha are emitted into the liquidity pool.

* [Tao emission](/docs/#distribution-of-emitted-tao)
* [Alpha Emission](/docs/alpha-emission)

Note that the value of k will change with each block as a result of this emission.

## Alpha Price

The subnet pool determines the alpha price (shown in tao).

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/eedd7d73e72dd141.png" />

> 📘 **If there is 100 tao\_in, and 100 alpha\_in, the α\_price will be 1 tao.**

## Subnet Pool Initialization

When a new subnet is registered, the pool is seeded from the [registration cost](/docs/subnet-registration): a portion of the lock cost is paid in as TAO (`tao_in`), and a matching amount of alpha is minted (`alpha_in`) to set the opening price. The remainder of the lock cost is recycled. The starting `alpha_price` is therefore the ratio of the seeded reserves.
