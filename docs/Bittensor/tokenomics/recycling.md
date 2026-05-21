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

> 📘 Recycled vs. burned
>
> **Recycled tao/alpha** just becomes unissued - ready to be emitted again at a later date
>
> **Burned tao/alpha** is destroyed. This token no longer exists, and cannot be used.

## Alpha token recycling

* **Neuron registration**: When a neuron is registered, the coldkey pays the registration fee in tao.  However, the fee is sent through the [subnet pool](doc:subnet-pools) and converted to alpha.  This alpha is then recycled.
* **Subsidized subnets**:  In certain conditions, excess tao is sold to alpha.  This alpha is then recycled.
* **Owner miners**: By default incentive to owner hotkeys is burned. But the owner can switch this to a recycle.

## Tao recycling

* **Root Neuron Registration**: If registering on root, there is no need to transfer the fee into alpha. The tao is directly recycled.
