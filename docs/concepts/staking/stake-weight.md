---
title: Stake weight
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

How to determine Validator stake weight.

With the launch of dTao, stakeholder may place stake on root or on a subnet.  In order to determine how much stake a validator has on a subnet, these values are combined.

Root stake is weighted at a lower value that the alpha stake.  The weighting parameter `tao_weight`  is defined on-chain (currently 0.18)

root\_stake: The amount of tao staked to a validator on root.\
tao\_weight : Defined on chain as 0.18.
alpha\_stake: The amount of alpha staked to a validator on the subnet
stake\_weight: The value used to determine emissions.

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/994be5fc7666f898.png" />

> 📘 **Example**
>
> <Image border={false} alt="Dark-themed table row with Child, Stake Weight, Root Prop, and Alpha Prop columns denominated in tao and alpha" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/7bb67d3e719651d8.png" />
>
> <Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/d542b1278004fb1d.png" />
