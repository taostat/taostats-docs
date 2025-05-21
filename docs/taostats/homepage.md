---
title: Taostats Home
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
The landing page of Taostats provides a a high level overview of several important aspects of the Bittensor network.

* [Tao Summary](#tao-summary)
* [Tao Trading Chart](#tao-trading-chart)
* [Subnet overview](#subnet-overview)
* [Subnet 0 data](#subnet-0-data)

# Tao Summary

Across the top of the homepage is a summary of the current trading state of the $TAO token.

<Image align="center" src="https://files.readme.io/ea6fb304425e873736152a3ff521ef7e5e9fb8e095b9512d6acfc590a75c9511-Screenshot_2024-09-06_at_14.56.12.jpg" />

* **Current price**: in USD (and daily change)
* **Market cap**: the value of all the **τ**  currently in circulation.
* **24h Volume**: How much **τ** was traded in the last day.
* **Circulating Supply**: **τ** that has been minted and can be traded.
* **Total Supply**: In \~2045, the final **τ** will be created, and there will be 21M TAO in circulation.

# Tao trading chart

This chart lists the historical price and trading volume of **τ**.  

* The price of **τ** is shown with an orange line.
* The daily volume is a blue bar chart, where each bar is one day's trading (in millions of USD).

**Chart controls:**

* **Plus and minus buttons:** zoom in and zoom out.
* **Magnifying glass**   select the zoom region

<Image align="center" width="75% " src="https://files.readme.io/7dcecce-Screenshot_2024-06-28_at_12.25.26.jpg" />

<br />

# Subnets overview

<br />

This summary of subnet data shows the top 8 subnets based on emission:

<Image align="center" src="https://files.readme.io/2425b199177d3048109e95f233eb12edc872a27477fb0366a5e921376f1f40fe-Screenshot_2024-09-06_at_14.57.09.jpg" />

# Validator Summary

A summary of the top 8 validators (based on stake).

![](https://files.readme.io/b3fd55748ddd1744c37cbb6b44a9633e0488f87ba64f5058d11a207a3cf5303d-image.png)

# Transactions

 Live listing of the last 10 transactions on chain

![](https://files.readme.io/f3dba5fb5c7b08eba6c8352ed5f5a1a4eb4df55d11b9632cdbadf283ea2d3915-image.png)

<br />

# Blocks

A live listing of the last 10 blocks emitted:

![](https://files.readme.io/5ddb333b37b2961c4e369c37db55754aa9d15a314594444831aeb2ad9620e516-image.png)

<br />

# Root metagraph

The chart at the bottom of the homepage shows data from the  [Root Subnet](doc:root-subnet) (Subnet 0.) Subnet zero is not used for mining.  Subnet 0 defines the allocation of emitted tao across the 32 subnets. 

## Validator data

* **POS**:  The position in the chart (not a ranking.)
* **Crown**: The crown indicates if the validator is a member of the Bittensor [Senate](doc:senate).
* **UID** The UID of the validator on Subnet 0.
* **Stake**: The TAO staked to that validator.
* **Hotkey** The hotkey for the validator.

## Validator Allocation

The remaining 33 columns list all of the subnets. Each validator divides their emissions allocation amongst the subnets. The sum for each validator will be 1.  The [Yuma Consensus](doc:consensus) will take the allocation from each validator, will weigh this ranking against their stake, and create an overall distribution for each subnet.  The result is shown at the top of each column below the subnet name.

Each column can be sorted in ascending or descending order.

> 📘 Example:
>
> <Image align="center" src="https://files.readme.io/b0c95e0ec4aef4282720b9ffc5ba5c337871a20b8514610e5500e53d382f0619-Screenshot_2024-09-06_at_15.00.15.jpg" />
>
> Validator in position 1 has allocated 9% of emissions to SN1
>
> Validator in position 2 has allocated 9% of emissions to SN1
>
> Validator in position 3 has allocated 0% to SN1.
>
> Across all of the validators, SN1 receives 7.07% of emissions. This is determined by [Yuma Consensus](doc:consensus).
