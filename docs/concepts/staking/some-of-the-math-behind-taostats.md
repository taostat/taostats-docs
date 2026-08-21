---
title: nom/1k/24BTday
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

This value represents the daily return in tao for every 1000 tao delegated.  We are sometimes a bit lax in the use of  "day" vs. "BTDay", but in all these cases, we mean 7200 blocks - which is approximately 24 hours.  (We are working to move to BTDay "Bittensor day" which is usually a few seconds longer than 24 hours).

The Basic calculation is:

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/913b073119086465.png" />

For validators, this must be calculated *per subnet* and then is added for a network-wide value.

On taostats, we are using actual returns from nominators on each validator to calculate a daily nom/1ktao/BTday. It accounts for Hotkey swaps, and other myriad ways that the calculation can be obfuscated on chain.

## Where you can find nom/1k/24BTday

* [Validator Home](https://taostats.io/validators)   This is the instantaneous value - from today's stats.
* [Staking Calculator](https://taostats.io/staking)  This is the 30 day average. This *smooths out* changes in the value that occur from changes in stake.
* [Validator Pages](https://taostats.io/validators/5GKH9FPPnWSUoeeTJp19wVtd84XqFW4pyK2ijV2GsFbhTrP1)  This is the sum of the value across all subnets.

![Dark-themed stat card displaying a nomination return per 1000 tao over 24 hours metric](/images/migrated/taostats-nom-per-1k-stat-card.png)

# Dominance

Dominance is calculated per subnet.  It is the validator stake/total tao staked on the subnet. If measured in the context of a subnet, a healthy validator (High VTrust/low updated) should have dividends that are similar to their dominance.

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/0ac48549efd956a5.png" />

This can be broken down a number of ways.

* **Child Hotkey dominance:** This is the sum of all child & parent stake/ total tao staked in the subnet.
* **Hotkey dominance:** Sum of all parent & child stakes for a single hotkey/total tao staked in the subnet.

# Daily Return

The amount that the validator has earned in the last 24 hours.  It is a sum of validator return across all subnets.

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/a62bcd176e1bc1b1.png" />

# Validator Return

To determine a validator's return in a subnet, we need to account for all places that emission is gained for validators  on the subnet:

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/7bc11e0e247c6f63.png" />

* Emission for the registered hotkey.

  * Calculate the % of stake held by the child hotkey \* the emission. (Note if there is no parent/child, the % of stake held is 100%)

    <Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/02a6fa53146c2032.png" />

* Child hotkey takes. If there is a child hotkey, they can extract a childkey take from parent hotkeys.  Find the emission of the parent hotkey, and multiply by the childkey take.  Sum for all parent hotkeys.

  <Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/3cd55593e151d069.png" />
* If the hotkey is a parent on one or more child hotkeys, calculate the parent return on other validator's child hotkeys, subtract the childkey take.  Sum these across all parents.

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/bfb7429f93920f30.png" />

These values, summed across the subnet, provide the validator return.

# APY: Annual Percentage Yield

nom/1k/24BTday is the DPY\*1000.  So, to get to APY, take any nom/1k/24BTday, and divide by 1000. The multiply by 365 to get the annual value.
