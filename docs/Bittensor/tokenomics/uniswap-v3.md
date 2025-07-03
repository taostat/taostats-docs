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

# Is Uniswap liquidity required?

No, Subnets can either use UniswapV3, or run on the existing Uniswapv2-like pools.  If the subnet is not on uniswapv3, there is no way to add liquidity into the pool outside of staking and emissions.

<br />

# Adding Liquidity

When a subnet has uniswapv3 active, holders of alpha and tao can add liquidity to the Subnet pool.  When adding liquidity, the user specifies a price range where they would like to support transactions on the pool.  In Uniswap, ranges are defined by `ticks`. Ticks define  a range of price where liquidity can be added.  Generally, you will be adding liquidity over a range of mant ticks (the price range in each tick is small.)

When a staking or unstaking event occurs in a tick where liquidity is set, the owner of the liquidity will earn a share of the staking fees paid by the staker/unstaker.  The earning is a weighted percentage based on the amount of liquidity in the tick across all liquidity holders.

<br />

# Setting Liquidity

Too add Liquidity to a subnet,

1. Open the subnet page on taostats. Below the trading view chart, you can select **Liquidity** in the  staking table.

![](https://files.readme.io/bd419a46775f87657315db8ec45d03b0b2cb8e37d8a83daa2f35bbe24ff2a0c7-image.png)

2. Set the price range that you would like to set for liquidity. The full range of prices is 0-infinity.  You can set a custom range as well:
3. ![](https://files.readme.io/bcfc4bea81c775a4b4d8a6a6f4fc1a6498272e8be31a8063add5fe09dbf97f22-image.png)

   ![](https://files.readme.io/ffa25ec6d2a8e0e9aef4431a227af220c81a36b14e90328db0be8f1adfaa9026-image.png)

   Deposit tokens.  If you are below the current price, you will only fund tao.  If you are bove the price, you will fuind alpha.  If the current price is in range, you will find tao & alpha.
4. Once set, all of your positions will be displayed in the tables below
5. ![](https://files.readme.io/1b5e4231a0207fdac28d59b1bfbaa86a2fd44d8a3f7b0435cc0934a600905604-image.png)

   ![](https://files.readme.io/eb116dc7d127a47ee054cf21be5249c3283df1fe3f2b039895ae70ef1e91cce6-image.png)

   <br />