---
title: Staking in dTao
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
Staking now plays a principal role in the functioning of the Bittensor network. The principal goal of dTao is to divide chain emissions amongst subnets in a democratic way.  

# Subnet emission

Emission into a subnet is determined by the amount of tao in the [Subnet Pool](doc:subnet-pools). The principal addition of tao into the pool is via staking actions. Therefore subnet emission is guided by how much stake has been placed on the subnet.

# Staking Options

in dTao, there are two options for staking:

- [Staking to root](#staking-to-root) 
- [Staking to a Subnet](#staking-to-alpha) 

> 📘 Staking fees
> 
> - Staking: All staking actions will incur a 50,000 rao (0.00005 tao) fee.
> - Unstaking:  
>   - Unstaking from root is set at 50,000 rao
>   - Alpha unskating: The minimum fee is 50,000 rao (0.00005 tao).  
>     - The max is a percentage of your alpha emission:
>     - AlphaEmission_epoch: the amount your coldkey earns in 360 blocks
>     - alpha_unstaked/alpha_staked = this is the % of alpha that you unstake.,
>     - alpha_price - the fee is paid in tao, so it is converted via the price.
>     - ![](https://files.readme.io/28fa9a6eacaebe6e2ddafd2c10a776896dcbb0bc2a8f92017cdb45083c480d4a-image.png)
> 
> Example unstaking:
> 
> You earn 10 alpha per epoch, and you unstake 50% of your alpha.  The fee will be 10_50% = 5 alpha_alpha_price

## Emission division: root to subnet

Stakeholder emission is split between these two options.  For new subnets, the emission is primarily to root, with subnet increasing over time

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3e9d7b5c3747867d7b1d97a068bfceb15d003e0f4ba498f2f5b48bcca74f11ac-image.png",
        null,
        "An example breakdown of root:subnet proportions."
      ],
      "align": "center",
      "caption": "An example breakdown of root:subnet proportions."
    }
  ]
}
[/block]


<br />

This change over time is described in [Emissions: Root vs. Alpha Stake](doc:stakeholder-emissions-root-vs-alpha). 

# Staking to root

The default action of staking to root is similar to what staking was pre-dTao.  All your earnings on each subnet are converted to tao and autocompound on root.  The default staking method on root is called `root stake`.

As seen in the section above, the initial emissions will be the same, but over time the `staking to root` returns will decrease (eventually reaching ~ 18% of original staking rewards).

If you have staked to root, your retruns will be autocompunded to your hotkey on root.

# Staking to alpha

This is the new feature and primary goal of dTao - to enable stakeholders to vote and determine the emissions for every subnet.

To stake in alpha, tao is exchanged via the [Subnet Pools](doc:subnet-pools) into alpha.  This will incur [Slippage](doc:slippage). The received alpha is then staked to the validator selected. 

<br />

## [dTao FAQ](doc:dtao-faq): Your top  staking questions