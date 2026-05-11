---
title: 'Tao Emission '
excerpt: Basics on how tao is emitted and distributed in Bittensor.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Every block, 1 tao is emitted by the chain (until 10.5M blocks are emitted and the first [Halving](doc:halving) occurs).  Where do these blocks go?

The tao is divided amongst the subnets and the fraction of tao awarded to each subnet is placed into the `tao_in` of the [Subnet Pools](doc:subnet-pools).
