---
title: Uniswap Subnet Pool Liquidity
excerpt: Uniswap V3 is a way to add liquidity to alpha subnet pools.
deprecated: false
hidden: false
metadata:
  robots: index
---
In summer 2025, uniswapV3 features will be added to Bittensor.

# Introduction

Every Subnet has a [Subnet Pool](doc:subnet-pools) that is used to exchage tao for the subnet alpha.  Prior to uniswapv3, all liquidity was added by token emission (each block, tao\_in from the % of tao distributed to the subnet and an equal value of alpha\_in.). Staking would add tao and reduce alpha, while unstaking would inxrease alpha and remove tao.

UniswapV3 allows investors to add additional liquidity into subnet pools. When their liquidity is used in staking/unstaking transactions, investores receive a portion of the staking fees paid.

> 📘 TL;dr
>
> Doug's thoughts on liquidity positions
>
> * You add tao/alpha into your liquidity position.  It's kind of like a limit order.  You set the range where you are happy to trade tao-> alpha (or alpha-> tao - both will happen). If you don't want to trade at a certain price - don't put it in your position  :thinking:
> * As the price changes (and it is inside your liquidity position), your tao/alpha ratios will change. As the price goes up, your alpha converts to tao, as the price goes down, your tao converts to alpha).
> * You get some of the fees every time there is a stake.
> * If the price goes out of the range you defined - your position will be 100% alpha (low price) or 100% tao (high price).  You'll no longer get fees. Your tao/alpha are not staked, so you are no longer earning.
> * If price is lower that your LP - you hold all alpha, and the price is dropping.. That could be bad.
> * If price is higher- you hold all tao, and none of that sweet sweet alpha that is appreciating. that could also be bad.

# Is Uniswap liquidity required?

No, Subnets can either use UniswapV3, or run on the existing Uniswapv2-like pools.  If the subnet is not on uniswapv3, there is no way to add liquidity into the pool outside of staking and emissions.

<br />

## Enabling Uniswap liquidity

To turn on user liquidity, Subnet owners must turn the `Enabled User Liquidity` hyperparameter to `true`.

# Adding Liquidity

When a subnet has uniswapv3 active, holders of alpha and tao can add liquidity to the Subnet pool.  When adding liquidity, the user specifies a price range where they would like to support transactions on the pool.  In Uniswap, ranges are defined by `ticks`. Ticks define  a range of price where liquidity can be added.  Generally, you will be adding liquidity over a range of mant ticks (the price range in each tick is small.)

When a staking or unstaking event occurs in a tick where liquidity is set, the owner of the liquidity will earn a share of the staking fees paid by the staker/unstaker.  The earning is a weighted percentage based on the amount of liquidity in the tick across all liquidity holders.

<br />

# Setting Liquidity

Too add Liquidity to a subnet,

1. Open the subnet page on taostats. Below the trading view chart, you can select **Liquidity** in the  staking table.

![](https://files.readme.io/bd419a46775f87657315db8ec45d03b0b2cb8e37d8a83daa2f35bbe24ff2a0c7-image.png)

2. Set the price range that you would like to set for liquidity. The full range of prices is 0-infinity.  You can set a custom range as well.  Note that the value may change slightly, asthe min & max prices must match a `tick` boundary.  Ticks are very small, so the difference is unlikely to make a large change.
3. ![](https://files.readme.io/bcfc4bea81c775a4b4d8a6a6f4fc1a6498272e8be31a8063add5fe09dbf97f22-image.png)

   Deposit tokens.  If you are below the current price, you will only fund tao.  If you are bove the price, you will fuind alpha.  If the current price is in range, you will find tao & alpha.

   ![](https://files.readme.io/d213505e380805b2a344b365177cf67fb2c335da4c1e181583cc1287b9d3e745-image.png)

<br />

4. Once set, all of your positions will be displayed in the tables below
5. ![](https://files.readme.io/1b5e4231a0207fdac28d59b1bfbaa86a2fd44d8a3f7b0435cc0934a600905604-image.png)

   ![](https://files.readme.io/e4e23a5cada9d14b3440662b144a35e0f4ac4c99483c79f96c4946ad98010f62-image.png)

   Once set, your positions will be used to buy and sell tao/alpha

![](https://files.readme.io/ed78a9be4abc0f953a16e8ae455db69829e6c0615ca6325a3f94556e44b83d04-image.png)

See all the positions by Clicking All Positions.

<br />

# What do you earn?

Every time a trade is made when the price is inisde your price window, you will receive a fraction of the staking fee (in tao) or the unstaking fee (in alpha).

There is no way on chain to determine your earnings while your position is open.

One position close, the swap.`remove_liquidity`  extrnisic is run.  This will close out the position.  The LIquidity Removed event will show the alpha and tao placed back into your wallet.  You  earn the `FeeAlpha` and `FeeTao` (shown in rao).

![](https://files.readme.io/bce7ffc6f3dca336323a1288f61fb0ce8decb8ffc4d18c122c5f814766a9c061-image.png)

<br />

As the price changes, the liquidity provided will shif.  If the price goes up, your alpha will be used, and tao will be added to your liquidity. As the price goes dow, your tao will be sold, and alpha will increase.