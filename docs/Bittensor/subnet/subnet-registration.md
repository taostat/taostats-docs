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

The registration cost is [recycled](doc:recycling)

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

# What happens to my alpha if a Subnet is Deregistered?

<br />

When a subnet is deregistered, all of the alpha is liquidated, and exchanged for tao from the pool.  This will be on your wallet as free tao.

<br />

For example:

If this subnet were to be deregistered: 1.88M alpha will be exchanged for 11,670 tao.

<Image border={false} src="https://files.readme.io/b62679ddc13e74d0dbda2ab2b82fed8324847bb88fc797c0a6f6afbfe78f7f51-image.png" />

<br />

Each alpha is worth 0.006 tao.

<Image border={false} src="https://files.readme.io/6de017365bea6725bfb775952f1765e130ff024b6f8b9803af25493a26caa0ef-image.png" />

<br />

If a Subnet's ADR is \< 1, holders will receive a premium - more tao that their alpha is currently worth (you can find each Subnet's ADR at [https://taostats.io/subnets](https://taostats.io/subnets) 

<Image border={false} src="https://files.readme.io/1e822e3def581b1c31eb141fb2f444d7969220215f7af58872089a47003a1220-image.png" />

<br />
