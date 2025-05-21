---
title: Tao Emission
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
Every block, 1 tao\* is emitted by the chain (until 10.5M blocks are emitted and the first halving occurs).  Where do these blocks go?

The tao is divided amongst the subnets and the fraction of tao awarded to each subnet is placed into the `tao_in` of the [Subnet Pools](doc:subnet-pools).

\*The amount of tao emitted each block is dependent on how much tao is emitted into each subnet pool. This can potentially be less than one.

## Determining the emission into each Subnet pool.

In the past, Subnet emissions were set by validators, and Yuma Consensus would aggregate the results based on validator stake and consensus.  This is no longer the case.

Tao emission (also known as `tao_in`) on a subnet is calculated by finding the subnet price, and dividing by the total of all subnet prices.

![](https://files.readme.io/2a743d39d2afaacc67b13c59c53b76b57ba794a23d89d4fea557fc1da1d76cb4-image.png)

> 📘 Tao\_in example:
>
> At dTao launch, 1 tao and 1 alpha will be added to the subnet pool for each of the 64 Subnets.
>
> Therefore, the alpha price is 1 tao/1 alpha  = 1.  This holds for all 64 subnets, so the tao\_in for each subnet at dTao launch is 1/64 = 0.015625 tao.
