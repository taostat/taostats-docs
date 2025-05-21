---
title: Taostats Landing page
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

![](https://files.readme.io/afa23e6-image.png)

* **Current price**: in USD (and daily change)
* **Market cap**: the value of all the **τ**  currently in circulation.
* **24h Volume**: How much **τ** was traded in the last day.
* **Circulating Supply**: **τ** that has been minted and can be traded.
* **Total Supply**: In \~2045, the final **τ** will be created, and there will be 21M TAO in circulation.
* **Validating APR**: Average APR across all subnets and validators.
* **Staking APR**:  The Validation APR, minus the 18% validator commission

# Tao trading chart

This chart lists the historical price and trading volume of **τ**.  

* The price of **τ** is shown with an orange line.
* The daily volume is a blue bar chart, where each bar is one day's trading (in millions of USD).

**Chart controls:**

* **Plus and minus buttons:** zoom in and zoom out.
* **Magnifying glass**   select the zoom region

<Image align="center" width="75% " src="https://files.readme.io/3cde9ef-taustats_zoom.gif" />

* **Hand**: Scroll left/right on zoomed-in data.
* **Home**: resets the chart

# Subnet overview

To the right of the trading chart is a table of all the subnets.  Click on a number, and you'll quickly see:

* **Active Keys**: Number of nodes on the subnet, and how many are active.
* **Active Validators**: Ratio of active validators out to total possible.
* **Dual Miners/Validators** : How many validators are also mining on the same hotkey.
* **Active Miners**: Number of active miners.
* **Registration cost**: The cost to register a node (as a validator or miner).

> 📘 <Image align="center" width="25% " src="https://files.readme.io/5c10a2c-image.png" />
>
> In this snapshot, Subnet 2 has 25 validators, 235 Miners (and 4 dual).  It would cost 0.63 TAO to register a node on this subnet.

# Subnet 0 Data

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
> ![](https://files.readme.io/6c7bee1-image.png)
>
> Validator in position 1 has allocated 9% of emissions to SN1
>
> Validator in position 2 has allocated 9% of emissions to SN1
>
> Validator in position 3 has allocated 0% to SN1.
>
> Across all of the validators, SN1 receives 7.07% of emissions. This is determined by [Yuma Consensus](doc:consensus).
