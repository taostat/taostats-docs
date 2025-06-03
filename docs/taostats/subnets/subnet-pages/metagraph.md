---
title: The Subnet Metagraph
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
The Subnet metagraph is a chart that displays a detailed readout of the neurons (validators & miners) on a subnet.

![](https://files.readme.io/4420f76a226bfaa643b2fa1c6962156db2db5f74cbe869eda0e077318f1fa8d4-image.png)

<br />

# Metagraph key

* **POS**: Position in the chart (not a ranking)
* **Shield/pickaxe**:
  * The shield icon is shown for all validators.
  * A pickaxe is shown for miners. Orange miners are in immunity. (Note: new validators might *initially* have a pickaxe until weights are set.)
* **UID**: Unique ID: A number 0-\{node count -1} that specifies the node the miner/validator is connecting on. Every miner or validator has a UID assigned to their registration.
* **Name**: The Hotkey name (if registered on the chain). Otherwise, the hotkey will be shown.
* **[Stake Weight](doc:stake-weight)**: Stake weight is a measurement of the alpha staked on the subnet.  Root stake is weighted at 18% of the tao staked.
  * Orange color: This validator has no parent hotkeys (see [Parent/Child Hotkeys](doc:emission-for-parentchild-hotkeys-copy))
  * Yellow Color: Validators that are [child hotkeys](#child-hotkeys).
* **VTrust**: *Validator* Measurement of [Validator](doc:validator) trust.  High Vtrust implies consensus on the weights being set by the validator.
* **Consensus**: *Miners*: A measurement of the consensus between the validators on the accuracy of the mining results. Adds to 1 for each subnet.
* **Incentive**: *Miners*: Represents the distribution of miner emissions. The emissions column adds to 1 for all miners.
* **Dividends** *Validators*: Breakdown of emissions per validator. Calculated from the amount of TAO staked and the Vtrust. Adds to 1 for each subnet
* **Emission**(P): Alpha granted each epoch (1 epoch is 360 blocks and approx 72 minutes). (Note: The metagraph from Bittensor outputs emission in 1 billionth of an alpha  per block. Same data, different units.).
* **Updated**
  * *Validator*:  The number of blocks since weights were last set. This should be less than 500 for optimum performance, and anything over 1500 triggers an alert.
  * *Miners* This value has no meaning for miners.
* **Axon**: IP address.
* **Hotkey**: Hotkey of the neuron.
* **Coldkey**: Coldkey of the neuron.
* **Root Stake**: Amount of tao staked on root
* **Root Weight**: Tao on root \* 18%
* **Alpha Stake** amount of alpha staked
* **Daily Alpha**: Daily rewards estimate in alpha.

<br />

## Child hotkeys

If a validator on the subnet is a child hotkey for other validators to parent on, *stake weight* will be yellow and have a carat. On clicking the carat, the stake weight will be broken down by the child and all of the parent hotkeys:

![](https://files.readme.io/9ddb7a892032fdde60912c83101004fe7bc0f48dfad1f8c39d89f9604f9df60a-image.png)

Opentensor is running the neuron, and is the child hotkey.The parents add stake to the child hotkey, giving the family sum (reported in the main metagraph.)

# Reading the metagraph

There is a ton of information here.  Here are a few tricks to read the metagraph:

## Validator view

### Columns of interest:

* **Stake** - The amount of tao delegated to the validator.
* **VTrust**: Vtrust describes how *in consensus* the validator's weights are.
* **Dividends/Incentive**: A percentage of validator & miner emissions that will be awarded to the neuron.
* **Emission/Daily rewards**:  Tao emissions per epoch (and extrapolated to per day)
* **Updated**: The number of blocks since last setting weights to ensure your validator is functioning correctly. A validator that is not setting weights will drop in vtrust and emissions.

Sort by stake (or rank) descending to display validators at the top of the table.

<Image align="center" alt="Subnet 18: 01/29/2024" border={false} caption="This chart lists the top 9 validators (by stake)." src="https://files.readme.io/38e8082-image.png" />

.

Some basic analysis points to help you better understand the data:

* **Mining and validating**: A single UID can run a miner and a validator. (Note: This is not true in all subnets)
  * Position 7 (UID 224) is mining in addition to validation (there are nonzero Trust/Consensus/Incentive values.)
* **Vtrust vs. Stake**. Validator emissions are defined by the amount staked and the Vtrust determined by the Yuma Consensus. Generally, higher numbers of stake & vtrust correlate directly to higher emission
  * **Vtrust effect**Positions 8&9 have nearly identical stake values.  Position 9 has a higher Vtrust (0.94 > 0.92). This leads to higher emissions (0.53 > 0.47.)
    * Vtrust is affected by how often weights are set (Updated lists the tao emitted since the last update.). Pe Position 8 has not updated weights on this network for 2657 (vs 298 for position 9), lowering their Vtrust score.
  * **High stake/low Vtrust**:  Position 3 has \~ 40k more tao staked than position 4.  Yet, it has lower Vtrust (0.91 vs 0.97). As a result, position 4 has *slighty* higher dividends and receives more emissions - despite the lower tao stake.

## Miner View

Sort the metagraph by incentive.  Your goal is to gain as much incentive as possible, as this directly correlates to emission.  (You can sort by emission, but this will also add validators into the mix.)

* Set the number of entries to 100.  We now see the bottom 100 nodes for emission (note, validators are here too - as they have 0 emission). Subtract away the validators, and the miners in immunity (gear icon), and the remaining miners are at risk of de-registration, as they have the lowest emission values.