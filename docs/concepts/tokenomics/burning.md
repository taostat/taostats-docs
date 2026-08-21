---
title: Tao
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

When token is burned - it is no longer accessible and not a part of the circulating supply

> 📘 **Recycled vs. burned**
>
> **Recycled tao/alpha** just becomes unissued - ready to be emitted again at a later date
>
> **Burned tao/alpha** is destroyed. This token no longer exists, and cannot be used.

* Tao extrinsic (transaction) fees are **recycled**, not burned — the tao is subtracted from total issuance and becomes available to be emitted again later (this defers the [halving](/docs/halving) slightly). Since runtime **445** the fee is also not paid to the block author. See [Recycling](/docs/recycling) and the [Runtime 445](/docs/runtime-445) explainer.

# Alpha

* Mining emission to the subnet owner hotkey is burned.
* Subnet owners can burn alpha
* Subsidized subnets: the validator alpha that would be converted to tao for root emissions is burned.
