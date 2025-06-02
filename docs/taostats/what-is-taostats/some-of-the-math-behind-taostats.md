---
title: Some of the Math Behind Taostats
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
# nom/1k/24BTday

This value represents the daily return in tao for everk 1000 tao delegated.  We are sometimes a bit lax in the use of  "day" vs. "BTDay", but in all these cases, we mean 7200 blocks - which is approximately 24 hours.  (We are working to move to BTDay "Bittensor day" which is usually a few seconds longer than 24 hours).

The Basic calculation is:

![](https://files.readme.io/d7b43cc8be4e847a94c7e844e3817c27da26b237c84bb00d0d0417f2a86a85f6-image.png)

For validators, this must be calculated *per subnet* and then is added for a network-wide value.

On taostats, we are using actual returns from nominators on each validator to calculate a daily nom/1ktao/BTday. It accounts for Hotkey swaps, and other myriad ways that the calculation can be obfuscated on chain.

## Where you can find nom/1k/24BTday

* [Validator Home](https://taostats.io/validators)   This is the instantaneous value - from today's stats.
* [Staking Calculator](https://taostats.io/staking)  This is the 30 day average. This *smooths out* changes in the value that occur from changes in stake.
* [Validator Pages](https://taostats.io/validators/5GKH9FPPnWSUoeeTJp19wVtd84XqFW4pyK2ijV2GsFbhTrP1)  This is the sum of the value across all subnets.

<Image align="center" width="25% " src="https://files.readme.io/3eb50ad88324a1b852029c3b6fcaa14be8c47326fea933e024b9b04630644933-image.png" />

# Dominance

Dominance is calculated per subnet.  It is the validator stake/total tao staked on the subnet. If measured in the context of a subnet, a healthy validator (High VTrust/low updated) should have dividends that are similar to their dominance.

![](https://files.readme.io/829e4eafbc8bdb963e388da971798571ef02c2fa4b01eba05c153285dcfa041c-image.png)

This can be broken down a number of ways.

* **Child Hotkey dominance:** This is the sum of all child & parent stake/ total tao staked in the subnet.
* **Hotkey dominance:** Sum of all parent & child stakes for a single hotkey/total tao staked in the subnet.

# Daily Return

The amount that the validator has earned in the last 24 hours.  It is a sum of validator return across all subnets.

<Image align="center" src="https://files.readme.io/449da9091d3d09eb781efaa4bc7c1efde5648d12bc3073486befbd5ec2130a35-Screenshot_2024-10-04_at_10.20.25.jpg" />

# Validator Return

To determine a validator's return in a subnet, we need to account for all places that emission is gained for validators  on the subnet:

<br />

<Image align="center" src="https://files.readme.io/c647dd1fd28a5f15b5f51d065865a9d90ac26e41de03f2c88cb2628d5e516b09-Screenshot_2024-10-04_at_10.21.49.jpg" />

* Emission for the registered hotkey.

  * Calculate the % of stake held by the child hotkey \* the emission. (Note if there is no parent/child, the % of stake held is 100%)

    <Image align="center" src="https://files.readme.io/c6cc5b7405f4a25f65b23433c98ce412cdf5612502f9f46ed8a3db06d458b291-Screenshot_2024-10-04_at_10.23.00.jpg" />

  <br />
* Child hotkey takes. If there is a child hotkey, they can extract a childkey take from parent hotkeys.  Find the emission of the parent hotkey, and multiply by the childkey take.  Sum for all parent hotkeys.

  <Image align="center" src="https://files.readme.io/f0fdd056330e6a62415dd7e418f135efd9955108e4c92782920179701c2757f9-Screenshot_2024-10-04_at_10.33.51.jpg" />
* If the hotkey is a parent on one or more child hotkeys, calculate the parent return on other validator's child hotkeys, subtract the childkey take.  Sum these across all parents.

<Image align="center" src="https://files.readme.io/8596497f169045e7dcd6086bd462091c47a11180b87a55e633f60d5980bebfd6-Screenshot_2024-10-04_at_10.34.37.jpg" />

These values, summed across the subnet, provide the validator return.

# APY: Annual Percentage Yield

nom/1k/24BTday is the DPY\*1000.  So, to get to APY, take any nom/1k/24BTday, and divide by 1000. The multiply by 365 to get the annual value.