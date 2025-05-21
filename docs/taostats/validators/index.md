---
title: Validators
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
The **[Validators](https://taostats.io/validators)** page lists statistics on the validators.

<br />

# Table

The validator table lists every validator, and some stats on the TAO staked to each validator:

* **Name**: The name of the Validator
* **Dominance**:  Describing alpha and tao stakes as compared to other validators. Adds to 1.
* **τ Rank**: Rank across all validators for root stake.
* **α Rank**: Rank across all validators for amount of alpha held
* **Noms** The number of nominators - both alpha and root.  Note: One wallet staking alpha on 30 subnets counts as 30 nominators.
* **24hr**: This is the change in nominators in the last 24 hours.
* **Active**: The number of subnets where the validator has a parent or child validator running.
* **Total Weight**: A weighted alpha value.  Tao staked on root is counted at 18% of alpha.
* **Root Stake**:  The amount of tao staked on root.
* **Alpha Stake** The amount of alpha staked across all subnets, converted into tao.
* **Take**: The percentage kept by the validator. The remainder is distributed to stakeholders.
