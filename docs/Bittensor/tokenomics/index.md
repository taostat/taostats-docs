---
title: Tokenomics & Emission
excerpt: >-
  Learn how tao and alpha tokens are emitted and distributed to participants on
  Bittensor.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
[Tao](doc:tao): The emission and distribution of tao into the subnets.

[Alpha Tokens](doc:alpha-tokens): Each subnet has a token that can be purchased with tao.

[Subnet Emission](doc:subnets-1): Alpha emission is divided between the participants and the subnet pool.

[Halving](doc:halving): Bittensor tokens (tao and alpha) follow the Bitcoin halving schedule.

[Recycling](doc:recycling): The purchase of a subnet or subnet neurons results in tao/alpah being recycled,

[Staking](doc:staking-in-dtao): Buy and sell alpha in each subnet. Or for a safer option, stake into the root subnet.

[Uniswap Subnet Pool Liquidity](doc:uniswap-v3): allows participants to add liquidity to subnet pools.

## Definitions:

* **Max Supply**: total number of tokens that will be issued.  For all Subnet alpha tokens and for tao, this is 21 million (each).
* **Total Supply**: Max Supply - burned.  We can never exceed total supply, some tokens are burned.
* **Burned**: Tokens that have been removed from circulation. A burn cannot be reversed - the token is eliminated.
* **Recycled**: Tokens that have been removed from circulation. These tokens can be issued again.
* **Circulating Supply**: Token that can be bought or sold.
  * For Subnets, this is a sum of alpha in the liquidity pool + all alpha that is staked.
  * For tao - this is all free tao and all staked tao.
* **Total Issuance**: Total of all tokens issued.  This is circulating supply + all token that is burned.