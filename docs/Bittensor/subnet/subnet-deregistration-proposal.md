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

In the August 12, 2025 OpenDev call, Const proposed adding deregistration again. For a subnet to be deregistered, it must be:

1. Out of immunity
2. NAV over 1.
3. Lowest price

This will likely change over time, and will be voted on by the Senate before it is put into place.

<br />

## Immunity

In the pre-dtao world, immunity was 7 days.  Today, Subnets can not even start emission for the first 7 days.  In the new proposal, subnets will be given adequate runway to get established and create a product.  The initial take was 6 months of immunity.

<br />

# Alpha Distribution Ration \< 1

Alpha Distribution Ration is defined as

![](https://files.readme.io/dd48fe231c72701bd107ccdbd8cb0f0c55075c40cfd26152241e94ccf241b295-image.png)

When ADR> 1 the alpha staked is worth more than tha alpha in the pool.  This means the subnet is more valuable than the assets in the pool.

When ADR \< 1, the assets in the pool are worth more than owning the subnet.  This places the subnet at risk of deregistration.  If the subnet were to be dissolved, the alpha owners would receive the tao\_in from the pool, which ahs a higher value than the alpha\_out.

ADR is listed on the subnet page, and each subnet's historical ADR is charted on the statistics page.

![](https://files.readme.io/8072f00db1e6ecc99a4fa9057f248d13c1ecb95a7c259100e7d1f6da19a7cf1a-image.png)

<br />

## Net Asset Value  (NAV)

NAV is no longer part of the deregistration planning.  However, NAV is simply the reciprocal of ADR.

![](https://files.readme.io/9671bb030caa463a9d42650d53764a71a46730b43b4587369d6dc5c1ef05f08d-image.png)

Substituting tao\_in/alpha\_in for price:

<br />

![](https://files.readme.io/68097d108b889b2dd75ba351ee5d8eefa38729b0f42ec0a11ff87057fa4c5e7c-image.png)

ADR = 1/NAV

<br />

## Lowest price

The subnet with the lowest price (and  would be the next to be deregistered.