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

The registration cost is [burned](doc:burning).

<br />

<GetMaxSubnets />

If the current maximum number of subnets has been reached, the lowest ranking subnet will be deregistered.

<br />

## Immunity

New subnets have 4 months of immunity.

# Subnet Deregistration 

## Deregistration History

Before dTao (Feb 2025), there was a competition on subnet activity, The subnet with the lowest emissions could be de-registered when a new subnet registered.

When dTao was launched, de-registration was removed from the chain

# Deregistration parameters

For a subnet to be deregistered, it must be:

1. Out of immunity
2. Lowest price

If there is a tie on the lowest price, the older subnet will be deregistered.

<Bottom5Subnets />

<br />

<br />

<br />

## Lowest price

The subnet with the lowest price would be the next to be deregistered.
