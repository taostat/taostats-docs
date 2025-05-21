---
title: Slippage
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
When buying or selling through a subnet (liquidity) pool, there is an inherent loss of value during the purchase called `slippage`.  

> 📘 The larger the purchase amount, the higher the slippage.

<br />

## What is slippage?

Due to the limited resources of the liquidity pool, any change in the ratio of tao/alpha will effect the price and exchange rate.  The act of making a purchase through the subnet pool changes the ratio, and effects the rate at which the exchange is placed.

> 📘 Slippage occurs when staking AND unstaking alpha.

## Slippage formulas

The tao/alpha conversion price cannot be used to calculate a transaction.  You must use the following equation to determine the `α_received`:

![](https://files.readme.io/e0922469b360cfe26334fd57ec386fc0df8beb1415beac58c8b0aca961cca4a6-image.png)

The opposite occurs when unstaking alpha to buy tao:

![](https://files.readme.io/51840061dfab59a6bd375a72a2d446003703456a6658f1098204b1ce17a62dfe-image.png)

The amount received will be less than the amount expected from the direct price conversion. The difference is denoted as slippage (generally shown as a percentage):

![](https://files.readme.io/2a735651eceede5e50fe54d00b883a166e7a99c20155ca1043f235aad9215bd8-image.png)

<br />

<br />

> 📘 Example 1 (large purchase = large slippage):
>
> A subnet pool has 100α and 100τ.  alpha:tao is 1:1, so the alpha price is 1 tao.
>
> ![](https://files.readme.io/b4b5fc63a0c2c45d90bba35e3287ce8a515f79f9440581edfb428297697a1a89-image.png)
>
> A tao holder wishes to sell 1,000 tao for alpha.  Following the exchange rate of 1:1, you might assume 1,000α would be received. But there is just 100α in the pool, so using the equation above 90.9α is received.
>
> This results in a slippage of 90.91%:
>
> <Image align="center" width="50% " src="https://files.readme.io/a7703a9684fe70152b2355f1579288d7525a4870028ae80934221c652f4b4fb1-image.png" />
>
> Large purchases of tao or alpha will have large amounts of slippage.

<br />

> 📘 Example 2 smaller purchase
>
> A subnet pool has 100α and 100τ.  alpha:tao is 1:1, so the alpha price is 1 tao.
>
> ![](https://files.readme.io/b4b5fc63a0c2c45d90bba35e3287ce8a515f79f9440581edfb428297697a1a89-image.png)
>
> A tao holder wishes to sell 10 tao for alpha.  Using the equation for alpha\_expected, they will receive 9.09α.
>
> This results in 9.1% slippage.
>
> <Image align="center" width="50% " src="https://files.readme.io/a4d6088065f7ee95b3202e22faaacaa15ce88dd5de06441895fe71114599fb65-image.png" />
