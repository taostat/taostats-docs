---
title: Subnet Registration/Deregistration
excerpt: >-
  In September 2025, Subnet registration and deregistration was added back to
  the chain
deprecated: false
hidden: false
metadata:
  robots: index
---
# Subnet Registration

Subnet registration is currently possible.  The cost to register a subnet is:

<SubnetCost />

The registration cost is burned.

<br />

<GetMaxSubnets />

If the current maximum number of subnets has been reached, the lowest ranking subnet will be deregistered.

<br />

# Subnet Deregistration History

Before dTao (Feb 2025), there was a competition on subnet activity, The subnet with the lowest emissions could be de-registered when a new subnet registered.

When dTao was launched, de-registration was removed from the chain

# Subnet current state

There are 128 subnets, but many are inactive, and the tao/alpha in these subnets is not being adequately utilized.

# Deregistration parameters

For a subnet to be deregistered, it must be:

1. Out of immunity
2. Lowest price

If there is a tie on the lowest price, the older subnet will be deregistered.

<br />

## Immunity

In the pre-dtao world, immunity was 7 days.  Today, Subnets can not even start emission for the first 7 days.  In the new proposal, subnets will be given adequate runway to get established and create a product.  The initial take was 6 months of immunity.

<br />

<br />

## Lowest price

The subnet with the lowest price would be the next to be deregistered.
