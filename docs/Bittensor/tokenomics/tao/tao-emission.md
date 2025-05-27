---
title: Tao Emission
excerpt: Basics on how tao is emiitted and distributed in Bittensor.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Every block, 1 tao\* is emitted by the chain (until 10.5M blocks are emitted and the first halving occurs).  Where do these blocks go?

The tao is divided amongst the subnets and the fraction of tao awarded to each subnet is placed into the `tao_in` of the [Subnet Pools](doc:subnet-pools).

\*The amount of tao emitted each block is dependent on how much tao is emitted into each subnet pool. This can potentially be less than one.

## Determining the emission into each Subnet pool.

In the past, Subnet emissions were set by validators, and Yuma Consensus would aggregate the results based on validator stake and consensus.  This is no longer the case.

Tao emission (also known as `tao_in`) on a subnet is calculated by finding the subnet price, and dividing by the total of all subnet prices.

![](https://files.readme.io/2a743d39d2afaacc67b13c59c53b76b57ba794a23d89d4fea557fc1da1d76cb4-image.png)

> 📘 Tao\_in example:
>
> If the Sum of all prices is 1.8, and the proce for a Subnet is 0.2.
>
> tao\_in will be 0.2/1.8 = .111 per block.