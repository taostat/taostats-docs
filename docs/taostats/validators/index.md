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

![](https://files.readme.io/1a7daac874d1b4b27d3d214cf102f57f2c20f7ca1a14fd7ecf45f1461153bb22-image.png)

<br />

# Table

The validator table lists every validator, and some stats on the TAO staked to each validator:

* **Name**: The name of the Validator
* **Dominance**:  Describing [Stake Weight](doc:stake-weight) as a percentage of all validator stake weights. Adds to 1.
* **Noms** The number of nominators - both alpha and root.  Note: One wallet staking alpha on 30 subnets counts as 30 nominators.
* **24hr**: This is the change in nominators in the last 24 hours.
* **Active**: The number of subnets where the validator has a parent or child validator running.
* **Total Weight**: A weighted tao value.  Tao staked on root is counted at 18%. All alpha is converted into tao.
* **Weight Change**: 24h change in Total Weight.
* **Root Stake**:  The amount of tao staked on root.
* **Alpha Stake** The amount of alpha staked across all subnets, converted into tao.
* **Take**: The percentage kept by the validator. The remainder is distributed to stakeholders.