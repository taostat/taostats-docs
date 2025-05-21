---
title: Alpha Tokens
excerpt: Updated January 28, 2025
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
in dTao, all subnets will have a token for staking. The subnet tokens are given a letter from an alphabet (greek, hebrew, arabic, etc.) but are generically defined as 'alpha'.  (alpha is also the token of subnet 1, as it is the first letter in the greek alphabet)

## Alpha tokens can only be purchased with tao.

Your staking transaction will take your tao to purchase alpha.  This is done through a liquidity pool. Since each subnet has a token, each subnet has a liquidity pool (or Subnet Pool) that converts tao to the token of the subnet

![](https://files.readme.io/112d6315e15b0a250a28c6efab46d1ae7baadf5e1c17f879aa6e422ea4fb1289-image.png)

In the screenshot above of the btcli, the P column shows the amount of tao and alpha available in the liquidity pools for subnets 255 and 2.  Subnet 2's pool has 21.65 tao and 5,170 beta.

## [Subnet Pools](doc:subnet-pools)

Subnet pools are how tao is exchanged into alpha.

## Alpha Price

The Subnet pool determines the alpha price

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d8bf29448d71b415d59c472a882819ef507178fbc4c005550ba647dd33f25e76-image.png",
        null,
        ""
      ],
      "align": "center",
      "sizing": "50% "
    }
  ]
}
[/block]


<br />

## [Slippage](doc:slippage)

When buying alpha (or unstaking/selling alpha), the alpha price is indicative of the amount you will receive, but every purchase has slippage.

## What are alpha tokens used for?

- Alpha is used for staking on a subnet. The more alpha staked, the higher the subnet's emissions
- Alpha is used to register neurons (miners & validators) on the subnet.  Alpha spent registering neurons is recycled.