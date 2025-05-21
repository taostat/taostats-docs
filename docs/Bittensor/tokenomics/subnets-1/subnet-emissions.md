---
title: 'Subnet Emission: tao and alpha'
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
# tao and alpha Emissions:

Every block:

- A fraction of the emitted tao is emitted into each subnet pool. This is referred to as `tao_in`.
  - See:[Tao Emission Distribution](doc:tao-emission)
- Alpha tokens (to a max of 2/block) split between the subnet pool and subnet stakeholders. 
  - See: [Alpha Emission](doc:alpha-emission)
    - alpha added to the subnet pool is called `alpha_in`.
    - alpha distributed to subnet stakeholders is called `alpha_out`.

# `tao_in`

- `tao_in` is determined by the subnet price divided by the sum of all subnet prices. See [Tao Emission](doc:tao-emission)

# alpha_in

- The amount of alpha added to the pool is equal in value to the amount of tao added in. However, alpha_in is capped at 1. [Alpha Emission](doc:alpha-emission)

# alpha_out

- Every block, 1 `alpha_out` is distributed amongst stakeholders.