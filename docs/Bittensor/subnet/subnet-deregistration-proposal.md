---
title: Subnet Deregistration Proposal
excerpt: In August 2025, a proposal was raised to reinstitute Subnet Deregistration
deprecated: false
hidden: false
metadata:
  robots: index
---
# Subnet Deregistration History

Before dTao (Feb 2025), there was a competition on subnet activity, The subnet with the lowest emissions could be de-registered when a new subnet registered.

When dTao was launched, de-registration was removed from the chain

# Subnet current state

There are 128 subnets, but many are inactive, and the tao/alpha in these subnets is not being adequately utilized.

# Proposal

In the AUgust 12, 2025 OpenDev call, Const proposed adding deregistration again. For a subnet to be deregistered, it must be:

1. Out of immunity
2. NAV over 1.
3. Lowest price

This will likely change over time, and will be voted on by the Senate before it is put into place.

<br />

## Immunity

In the pre-dtao world, immunity was 7 days.  Today, Subnets can not even start emission for the first 7 days.  In the new proposal, subnets will be given adequate runway to get established and create a product.  The initial take was 6 months of immunity.

<br />

# Net Asset Value >1

Net Asset Value (NAV) is a companies assets minus liabilities, divided by the number of shares.

![](https://files.readme.io/ba99d6f7e87cb3bcd26a9d9bc26039b0cb4aee2ebd41118a85bef5ca46249353-image.png)

For a Subnet, this looks like:

tao\_in is a sum of all the assets in the subnet.  The shares are the alpha owned by subnet participants (and converted to tao to ensure both are reported in the same units).

![](https://files.readme.io/26615e1101312b8e29436c567650286203c8e47f88454ce09e8bfb1eaea98392-image.png)

If NAV >1, this means that the value of tao in the pool is greater than the value of alpha held by shareholders.

<Callout icon="📘" theme="info">
  A subnet has 100 tao\_in, but the alpha\_out is worth 50 tao (alpha\_out \* price).

  * NAV is 2, and the subnet could be deregistered.
  * When the subnet is liquidated, they will receive alpha\_out\_price\_NAV tao.

  If a holder has 1 tao worth of alpha, they will receive 2 tao on liquidation - increasing the value of their holding.
</Callout>

To see a subnets Historical NAV,

## Lowest price

The subnet with the lowest price (and  would be the next to be deregistered.