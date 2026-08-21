---
title: Alpha tokens
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

Alpha is the generic name for subnet tokens.  Each subnet has its own token.

From the dTao launch in February 2025, all subnets now have a token for staking. The subnet tokens are given a letter from an alphabet (greek, hebrew, arabic, etc.) but are generically defined as 'alpha'.  (alpha is also the token of subnet 1, as it is the first letter in the greek alphabet)

## [Alpha Emission](/docs/alpha-emission)

## Alpha tokens can only be purchased with tao.

Your staking transaction will take your tao to purchase alpha.  This is done through a liquidity pool. Since each subnet has a token, each subnet has a liquidity pool (or Subnet Pool) that converts tao to the token of the subnet.  The price cannot be used to determine the exact conversion, there is [Slippage](/docs/slippage) on every transaction in and out of a Subnet Pool.

## [Subnet Pools](/docs/subnet-pools)

<Image border={false} alt="Liquidity pool readout showing alpha and tao reserves with equal USD values and a stacked proportion bar splitting the pool by token count" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/31237355941bfdf3.png" />

In the screenshot above, the value of alpha and tao in the pools are equal, but there are \~4x the alpha tokens in the pool vs. tao.  Alpha Price is determined by the contents of the subnet pool.

## Alpha Price

The Subnet pool determines the alpha price:

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/eedd7d73e72dd141.png" />

> 📘 **Example**
>
> Using the pool in the screenshot above. 110,900/432,470= 0.2564.  This is the price of Subnet 64 when the screenshot was taken.

## [Slippage](/docs/slippage)

When buying alpha (or unstaking/selling alpha), the alpha price is indicative of the amount you will receive, but every purchase has slippage.

## What are alpha tokens used for?

* Alpha is used for staking on a subnet. The more alpha staked, the higher the subnet's emissions
* Alpha is used to register neurons (miners & validators) on the subnet.  Alpha spent registering neurons is recycled.

## Related

* [Alpha emission](/docs/alpha-emission) — how `alpha_in` and `alpha_out` are minted each block.
* [Subnet Pools](/docs/subnet-pools) — the liquidity pool that sets the alpha price.
* [Price Impact and Slippage](/docs/slippage) — why the quoted price isn't the exact amount you receive.
* [Staking in dTao](/docs/staking-in-dtao) — how to stake tao into a subnet's alpha.
* [Subnet emission overview](/docs/split-alpha-out) — how emitted alpha is split across participants.
