---
title: Basic data
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

Each validator has a page with details on validation.

In dTao, stakeholders must choose both a subnet to stake into, but which validator instide that subnet to stake on.

Each validator in a subnet is graded. If their weights are in [Yuma Consensus](/docs/consensus) with other validators, they will earn a high VTrust score, and a higher percentage of the emissions (Dividends).

<Image border={false} alt="Validator dashboard cards showing total stake weight with a root/alpha split bar, nominator and validator return, total nominators, dominance, and identity sidebar" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/f5978ae5d0c635b6.png" />

At the top of every validator page, some basic data is delivered:

* **Tao Stake Weight**: This is a weighted total of stake  tao\_staked\*root\_weight + alpha\_staked
  * In the screenshot above 773k tao on root is 139k weighted.  39k alpha
  * This gives a 78/22 % breakdown to tao to alpha
* **Nominator Return**: Total earnings per day, across all subnets in tao.
* **Validator Return** Actual earnings by the validator, based on the take % indicated.
* **Total Nominators**: Number of stakeholders on this validator
* **Dominance** : % of all stake controlled by this validator.

<Image border={false} alt="Validator detail tab bar with Performance, Staked, Rewards, and Legacy Weights tabs (Performance active)" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/e1dd9a7d4b17e905.png" />

# Performance

The performance tab gives the validator feedback on how well the validator is performing in a subnet. A row highlighted in red is not performaning well, and should be investigated:

<Image border={false} alt="Validator performance table with rank, key, name/address, percentage metrics, tao stake, a root/alpha split bar, and a count column, one row highlighted red as underperforming" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/ff1a68e4d870379f.png" />

## Performance Columns:

* **Netuid**: The subnet
* **Type:**.
  * Key: Parent hotkey
  * Server: running infra
* **CK Take**: The child hotkey take of the child hotkey
* **Proportion**: Percentage of stake that is assigned to this key.

> 📘 <Image border={false} alt="Dark-themed table with Netuid, Type, Hotkey, CK Take, Proportion, and Subnet Weight columns plus a root/alpha proportion bar defining performance metrics" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/79cdeed51afe6ffd.png" />
>
>   In Subnet 1, this validator has 90% of their stake on opentensor foundation, and 10% at 5Cg5Q...

* **Subnet Weight**: How much weighted alpha this validator holds.

> 📘 **Weighted alpha**
>
> Staked tao is weighted at 18%, If a Validator has 555,555 tao and 100,000 alpha:
>
> <Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/1013a83de277a753.png" />
>
> The Subnet weight is 200,000

* **Subnet Balance**: A percentage of tao vs alpha for the validator.
* **Noms**: Number of nominators on the Subnet
* **Family Weight**:  This is the weighted alpha for all parents/children on the active hotkey
* **Family Balance**: The ratio of tao:alpha held by all parents and children on the active hotkey
* **Dominance**:  Th fraction of emissions controlled by this validator family.
* **Divs**:  the Dividends received by the family.  With high VTrust, Dominanace and Divs should be similar.
* **UID** Neuron ID of the Validator in the Metagraph.
* **Pos**:
* **VTrust**: VTRUST of the child validator
* **Updated**: Number of blocks since weights were last set

# Staked

A chart showing tao staked over time & the number of nominators

<Image border={false} alt="Dual-axis time-series chart plotting number of nominators on the left axis and total tao staked on the right axis over time" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/f97d3360b4ac4efe.png" />

## Nominator search

a table with the top stakeholders. Sort by Subnet or by account.

<Image border={false} alt="Nominator search table with Account (avatar plus address), Subnet ID, Alpha, and TAO columns, plus subnet filter, search, row-count, and CSV controls" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/2d22b6fbc57f12bb.png" />

# Rewards

nom/1k/day - root

<Image border={false} alt="Dual-axis time-series chart plotting nominators per thousand tao (7-day moving average) against validator take percentage over time" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/5b7c1296e97d54de.png" />
