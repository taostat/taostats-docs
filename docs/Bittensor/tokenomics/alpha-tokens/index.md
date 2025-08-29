---
title: Alpha Tokens
excerpt: Alpha is the genearic name for subnet tokens.  Each subnet has its own token.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
From the dTao launch in February 2025, all subnets now have a token for staking. The subnet tokens are given a letter from an alphabet (greek, hebrew, arabic, etc.) but are generically defined as 'alpha'.  (alpha is also the token of subnet 1, as it is the first letter in the greek alphabet)

## [Alpha Emission](doc:alpha-emission)

## Alpha tokens can only be purchased with tao.

Your staking transaction will take your tao to purchase alpha.  This is done through a liquidity pool. Since each subnet has a token, each subnet has a liquidity pool (or Subnet Pool) that converts tao to the token of the subnet.  The price cannot be used to determine the exact conversion, there is [Slippage](doc:slippage) on every transaction in and out of a Subnet Pool.

<br />

## [Subnet Pools](doc:subnet-pools)

<Image align="center" border={false} caption="The subnet pool for SN 64 (May 28, 2025)" src="https://files.readme.io/7fdbb36d142a090808c56e253f6170a58198dee773f137c845ab15631086d8e4-image.png" />

In the screenshot above, the value of alpha and tao in the pools are equal, but there are ~4x the alpha tokens in the pool vs. tao.  Alpha Price is determined by the contents of the subnet pool.

<br />

<Subnetpools />

## Alpha Price

The Subnet pool determines the alpha price:

Note: that for subnets with uniswapv3 enabled, the alpha price is stored as the square root of alpha price. This is done to preserve accuracy on [Uniswap V3](doc:uniswap-v3) calculations.

<br />

<Image align="center" width="50% " src="https://files.readme.io/d8bf29448d71b415d59c472a882819ef507178fbc4c005550ba647dd33f25e76-image.png" />

> 📘 Example
>
> Using the pool in the screenshot above. 110,900/432,470= 0.2564.  This is the price of Subnet 64 when the screenshot was taken.

## [Slippage](doc:slippage)

When buying alpha (or unstaking/selling alpha), the alpha price is indicative of the amount you will receive, but every purchase has slippage.

<br />

## What are alpha tokens used for?

* Alpha is used for staking on a subnet. The more alpha staked, the higher the subnet's emissions
* Alpha is used to register neurons (miners & validators) on the subnet.  Alpha spent registering neurons is recycled.
