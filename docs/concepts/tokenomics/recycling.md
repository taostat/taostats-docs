---
title: Recycling
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

Recycling is the process of returning active tao or alpha to the unissued pool.

> 📘 **Recycled vs. burned**
>
> **Recycled tao/alpha** just becomes unissued - ready to be emitted again at a later date
>
> **Burned tao/alpha** is destroyed. This token no longer exists, and cannot be used.

## Alpha token recycling

* **Neuron registration**: When a neuron is registered, the coldkey pays the registration fee in tao.  However, the fee is sent through the [subnet pool](/docs/subnet-pools) and converted to alpha.  This alpha is then recycled.
* **Subsidized subnets**:  In certain conditions, excess tao is sold to alpha.  This alpha is then recycled.

## Tao recycling

* **Root Neuron Registration**: If registering on root, there is no need to transfer the fee into alpha. The tao is directly recycled.
* **Subnet Registration**:  When a subnet is registered, 1 tao from the fee is placed in the subnet pool. If there is any lock fee remaining, it is recycled.
* **Transaction fees**: Extrinsic (transaction) fees are recycled — subtracted from total issuance and available to be emitted again later, rather than paid to the block author. Since runtime **445** this reverted the earlier behaviour of rewarding the block author. Alpha-denominated fees are sold to tao and that tao is recycled. See the [Runtime 445](/docs/runtime-445) explainer.
