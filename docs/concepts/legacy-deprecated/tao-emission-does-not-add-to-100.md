---
title: The chain is buying this tao and injecting it into subnet Liquidity pools.
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

Learn about tao excess and how it is calculated.

Looking at the Taostats Subnet page, you may notice that the Emissions do not always add to 100%

<Image border={false} alt="Dark-themed subnet table with rank, subnet, tags, and a single emission-percentage column plus a total row summing less than 100%" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/4a59cd329b585737.png" />

If 1 tao is emitted per block, this means that just 0.817 tao is being awarded to subnets. Where is the other .183 tao going?

## Why??

[Tao Emission](/docs/tao-emission) is calculated from EMA flow.

[Alpha Emission](/docs/alpha-emission) is calculated from tao emission and price - but it has a max value of 1.

At the time of writing, Subnet 8 has:

* a normalized EMA flow of 0.05635527424782002.
* Price is 0.035997

This would mean that alpha\_in should be 1.55

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/f5379bd0d5b98e43.png" />

But since the maximum alpha that can be emitted into the pool is one, this is not possible.

So we reset alpha\_in to 1, and calculate the tao\_in:

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/3c1acd48067a61d3.png" />

The tao\_in cannot exceed 0.035997.

We have what is called `excess tao`  = default\_tao\_in - tao\_in

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/a12c352649f1902c.png" />

On SN 8 there is 0.0204 excess tao per block.

This tao is added to the liquidity pool, and the received alpha is recycled.

This serves to increase the price to nearer the emission percentage.

# how can I find which are getting excess tao?

On the taostats subnet page - look for the daily chain buy column. This is the per block value multiplied by 7200.

<Image border={false} alt="Single dark-themed table column headed "Daily Chain Buys" listing tao values in descending order with a sort chevron" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/a6dc50d6d18547bd.png" />

# how will Excess tao change after the halving?

When tao halves in December 2025, all excess tao will drop to 0.  Tao emissions will drop by 50%, and the max alpha\_in will still be 1.  This means that it is unlikely for excess toa be become a concern until we begin seeing alpha halvings in 2028.
