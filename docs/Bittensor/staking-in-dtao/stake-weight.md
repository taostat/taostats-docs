---
title: Stake Weight
excerpt: How to determine Validator stake weight.
deprecated: false
hidden: false
metadata:
  robots: index
---
With the launch of dTao, stakeholder may place stake on root or on a subnet.  In order to determine how much stake a validator has on a subnet, these values are combined.

Root stake is weighted at a lower value that the alpha stake.  The weighting parameter `tao_weight`  is defined on-chain (currently 0.18)

root_stake: The amount of tao staked to a validator on root.  
tao_weight : Defined on chain as 0.18.
alpha_stake: The amount of alpha staked to a validator on the subnet
stake_weight: The value used to determine emissions.

<Image border={false} src="https://files.readme.io/71b00711a2beb61987a3e73b3afbca9206f2ac8f74974a86fea6e12f56ac35bc-image.png" />

> 📘 Example
>
> <Image border={false} src="https://files.readme.io/bb194ac17c496bf4fbae84141955ccdbcaf6c235349854c93351423e1f2ae0a3-image.png" />
>
> <Image border={false} src="https://files.readme.io/b6a29fd4a881dee33f4eb5ceb0934cb4b258f0ed60f023c93a7612abf38bf2c4-image.png" />
