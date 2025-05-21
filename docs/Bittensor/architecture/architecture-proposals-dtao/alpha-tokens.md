---
title: Alpha Tokens
excerpt: Updated January 10, 2025
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
in dtao, all subnets will have a token for staking. The subnet tokens are given a letter from an alphabet (greek, hebrew, arabic, etc.) but are generically defined as 'alpha'.  (alpha is also the token of subnet 1, as it is the first letter in the greek alphabet)

## Alpha tokens can only be purchased with tao.

Your staking transaction will take your tao to purchase alpha.  This is done through a liquidity pool. Since each subnet has a token, each subnet has a liquidity pool (or Subnet Pool) that converts tao to the token of the subnet

![](https://files.readme.io/112d6315e15b0a250a28c6efab46d1ae7baadf5e1c17f879aa6e422ea4fb1289-image.png)

In the screenshot above of the btcli, the P column shows the amount of tao and alpha available in the liquidity pools for subnets 255 and 2.  Subnet 2's pool has 21.65 tao and 5,170 beta.

# Subnet Pools

The subnet pool is a critical part of staking into a subnet.  It is used to convert your tao into alpha.

## Alpha Price

The Subnet pool determines the alpha price

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e93ac9657306c2f490f90dc3abb60ede6d2605aa3d873c0688d19bbdae6bf41b-image.png",
        null,
        ""
      ],
      "align": "center",
      "sizing": "50% "
    }
  ]
}
[/block]


Using subnet 2 above, we use the tao_in and the alpha_in to calculate the price of the token. 

![](https://files.readme.io/5fc3a62a2c8b59693cc6a92164a6e29e686f65a2e1143d16cda289c78b2cc210-image.png)

## Slippage

When buying or selling through a liquidity pool, there is an inherent loss during the purchase called slippage.  The larger the purchase amount, the higher the slippage.

The values in the pool equal a constant.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3728ef5f4bae5d0725873f64c2bf6f8b078b8157cd91dea86e938bceb6052fed-image.png",
        null,
        ""
      ],
      "align": "center",
      "sizing": "50% "
    }
  ]
}
[/block]


If you buy alpha, this constant remains the same, so the actual amount of alpha purchased uses the following equation:

![](https://files.readme.io/e0922469b360cfe26334fd57ec386fc0df8beb1415beac58c8b0aca961cca4a6-image.png)

When you unstake alpha for tao, you will also incur slippage

![](https://files.readme.io/51840061dfab59a6bd375a72a2d446003703456a6658f1098204b1ce17a62dfe-image.png)

> 📘 Calculating Slippage
> 
> If you buy alpha, you will incur slippage - the price is effected by you buying alpha.
> 
> Say you bought 1 tao of subnet 2. Using the numbers above, you might expect to receive:
> 
> ![](https://files.readme.io/ff4438531d9cff19054e9615dda4d2067f7157d2434c07e0a0997d323b8c46e3-image.png)
> 
> But, your purchase of alpha modifies the price, and you will receive ~ 10 alpha less than you expect
> 
> ![](https://files.readme.io/93f99e5da8fd3d2fc4c5e4f89fd99b2b5bbda944dfe49b7915282b715aa5fa36-image.png)
> 
> Your slippage is the % difference. In this example - 4.4% slippage.
> 
> ![](https://files.readme.io/8db9dfe57aff3137fc2ff469c2b93ed86d07dd9cc37e5b384ba1e9de017eef65-image.png)