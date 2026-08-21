---
title: Table
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

<Image border={false} alt="Taostats validators page table with rank, name, dominance, nominators, 24h change, active, total weight, stake, root/alpha split, and take columns plus search and export controls" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/e8e2b583de29729d.png" />

The validator table lists every validator, and some stats on the TAO staked to each validator:

* **Name**: The name of the Validator
* **Dominance**:  Describing [Stake Weight](/docs/stake-weight) as a percentage of all validator stake weights. Adds to 1.
* **Noms** The number of nominators - both alpha and root.  Note: One wallet staking alpha on 30 subnets counts as 30 nominators.
* **24hr**: This is the change in nominators in the last 24 hours.
* **Active**: The number of subnets where the validator has a parent or child validator running.
* **Total Weight**: A weighted tao value.  Tao staked on root is counted at 18%. All alpha is converted into tao.
* **Weight Change**: 24h change in Total Weight.
* **Root Stake**:  The amount of tao staked on root.
* **Alpha Stake** The amount of alpha staked across all subnets, converted into tao.
* **Take**: The percentage kept by the validator. The remainder is distributed to stakeholders.
