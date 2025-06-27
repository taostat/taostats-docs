---
title: Uniswap V3
excerpt: Uniswap V3 is a way to add liquidity to alpha subnet pools.
deprecated: false
hidden: false
metadata:
  robots: index
---
In summer 2025, uniswapV3 features will be added to Bittensor.

UniswapV3 allows investors to add liquidity innto the subnet pools, and as a result earn rewards when their liquidity is used in staking/unstaking transactions.  Subnets can either use UniswapV3, or run on the existing Uniswapv2-like pools.  If the subnet is not on uniswapv3, there is no way to add liquidity into the pool outside of staking and emissions.

## Adding Liquidity

When a subnet has uniswapv3 active, holders of alpha and tao can add liquidity to the Subnet pool.  When adding liquidity, the user specifies a price range where they would like to support transactions on the pool.

If a staking or unstaking event occurs in that range, the liquidity holder will receive a portion of the staking fee (based on the percentage of liquidity held.)