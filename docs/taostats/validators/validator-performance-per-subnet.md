---
title: Validator Performance
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

Each validator in a subnet is graded. If their weights are in [Yuma Consensus](doc:consensus) woth other validators, they will earn a high VTrust score, and a higher percentage of the emissions (Dividends).

# Basic data

![](https://files.readme.io/850b15c4234db7d04aa9edcd352bc59b77fe789636d72d68a3f236bace457e3b-image.png)

At the top of every validator page, some basic data is delivered:

* **Tao Stake Weight**: This is a weighted total of stake  tao\_staked\*root\_weight + alpha\_staked
  * In the screenshot above 773k tao on root is 139k weighted.  39k alpha
  * This gives a 78/22 % breakdown to tao to alpha
* **Nominator Return**: Total earnings per day, across all subnets in tao.
* **Validator Return** Actual earnings by the validator, based on the take % indicated.
* **Total Nominators**: Number of stakeholders on this validator
* **Dominance** : % of all stake controlled by this validator.

![](https://files.readme.io/516b3e125fc4bb2b397e543e293ed992c820cc06dc8d8f8bf4719933adf732ee-image.png)

<br />

# Performance

The performance tab gives the validator feedback on how well the validator is performing in a subnet. A row highlighted in red is not performaning well, and should be investigated:

![](https://files.readme.io/8876560e4a4de0735d6f0cef3ab4a15acd155671613d53e4033185ca2a2517d8-image.png)

## Performance Columns:

* **Netuid**: The subnet
* **Type:**. 
  * Key: Parent hotkey
  * Server: running infra
* **CK Take**: The child hotkey take of the child hotkey
* **Proportion**: Percentage of stake that that is assigned to this key.

> 📘
>
> ![](https://files.readme.io/fcfa1e8c6ac937168dcacea0f5ab0a7edc073b3beb7a4818c0e338127c7b9bf6-image.png)
>
> In Subnet 1, this validator has 90% of their stake on opentensor foundation, and 10% at 5Cg5Q...

* **Subnet Weight**: How much weighted alpha this validator holds.

> 📘 Weighted alpha
>
> Staked tao is weighted at 18%, If a Validator has 555,555 tao and 100,000 alpha:
>
> ```
> Subnet Weight = .18*555,555 + 100,000
>               = 100,000 + 100,000
>               = 200,000
> ```
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

![](https://files.readme.io/5a09a7bde1ef1f4131346f007eec4572acd59a5d79d5569ab1c7c9e946b37968-image.png)

# Rewards

nom/1k/day - root

![](https://files.readme.io/3307778bcc33d616f43f52b77014ebc6638a46e137e413945da236deb2670da9-image.png)
