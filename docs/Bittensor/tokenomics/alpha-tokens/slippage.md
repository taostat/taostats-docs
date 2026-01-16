---
title: Price Action and Slippage
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
When buying or selling through a subnet (liquidity) pool, there is an inherent loss of value during the purchase called `Price Action`.

Additionally, there can be unexpected changes to the price (due to other trades, or factors that change the subnet price.  This is known as `Slippage`.

<br />

> 📘 The larger the purchase amount, the higher the price action
>
> ### The smaller the liqudity pool, the higher the price action.

## What is Price Action?

Due to the limited resources of the liquidity pool, any change in the ratio of tao/alpha will effect the price and exchange rate.  The act of making a purchase through the subnet pool changes the ratio, and effects the rate at which the exchange is placed.

> 📘 Price Action occurs when staking AND unstaking alpha.

## What is Slippage?

Slippage occurs when **additional** changes effect the subnet price, and chnage the amount of tao/alpha received.  For example, a transaction may have 0.5% Price Action, but another stake occurs, changing the price, adding a 0.25% Slippage. The entire change is Price Action + Slippage (in our example (0.75%).

## Price Action & Slippage formulas

The tao/alpha conversion price cannot be used to calculate a transaction.  You must use the following equation to determine the `α_received`:

<Image border={false} src="https://files.readme.io/e0922469b360cfe26334fd57ec386fc0df8beb1415beac58c8b0aca961cca4a6-image.png" />

The opposite occurs when unstaking alpha to buy tao:

<Image border={false} src="https://files.readme.io/51840061dfab59a6bd375a72a2d446003703456a6658f1098204b1ce17a62dfe-image.png" />

The amount received will be less than the amount expected from the direct price conversion. The difference is denoted as slippage+price action (generally shown as a percentage):

<Image border={false} src="https://files.readme.io/2a735651eceede5e50fe54d00b883a166e7a99c20155ca1043f235aad9215bd8-image.png" />

<Callout icon="📘" theme="info">
  NOTE: Slippage is calculated slightly differently in subnets with [Uniswap Subnet Pool Liquidity](doc:uniswap-v3) activated.  The basics still hold, but if buying and selling in a range with a lot of liquidity, the sippage will be **lower** than the calculations above.
</Callout>

<br />

## Price Action Calculator

<SlippageCalculator />

<br />

> 📘 Example 1 (large purchase = large price action):
>
> A subnet pool has 100α and 100τ.  alpha:tao is 1:1, so the alpha price is 1 tao.
>
> <Image border={false} src="https://files.readme.io/b4b5fc63a0c2c45d90bba35e3287ce8a515f79f9440581edfb428297697a1a89-image.png" />
>
> A tao holder wishes to sell 1,000 tao for alpha.  Following the exchange rate of 1:1, you might assume 1,000α would be received. But there is just 100α in the pool, so using the equation above 90.9α is received.
>
> This results in a price action of 90.91%:
>
> <Image align="center" border={false} width="50% " src="https://files.readme.io/a7703a9684fe70152b2355f1579288d7525a4870028ae80934221c652f4b4fb1-image.png" />
>
> Large purchases of tao or alpha will have large amounts of price action.

<br />

> 📘 Example 2 smaller purchase
>
> A subnet pool has 100α and 100τ.  alpha:tao is 1:1, so the alpha price is 1 tao.
>
> <Image border={false} src="https://files.readme.io/b4b5fc63a0c2c45d90bba35e3287ce8a515f79f9440581edfb428297697a1a89-image.png" />
>
> A tao holder wishes to sell 10 tao for alpha.  Using the equation for alpha_expected, they will receive 9.09α.
>
> This results in 9.1% price action.
>
> <Image align="center" border={false} width="50% " src="https://files.readme.io/a4d6088065f7ee95b3202e22faaacaa15ce88dd5de06441895fe71114599fb65-image.png" />

<br />

## Price Action and Slippage values

The transaction tables list the actual slippage of a transaction.  A negative slippage means your transaction actually profited from the trade

<Image border={false} src="https://files.readme.io/17ff300d55f73503d339d2de784d3edca266536ebbdb3304891f08701e8dc4e6-image.png" />
