---
title: Calculator
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
The [Delegation/Staking](https://taostats.io/staking/) link in the header opens a tao staking/validation calculator:

<Image align="center" width="75% " src="https://files.readme.io/bad9695-Screenshot_2024-06-24_at_08.35.45.jpg" />

To use the calculator, enter the amount of tao you wish to stake, the validatopr you wish to stake with. Most users will leave the checkbox at "Staker."

* Staker vs. Validator:  As a staker - a percentage of the emissions are given to the validator ('take').  This is subtracted from the total.  As a validator, you will earn both emissions & take.

Results:

* Daily Staking return - for the validator chosen, the amount of tao that will be added to your hotkey.
* Monthly Staking return.- Estimates monthly return by multiplying the daily figure by 30. (Note: there will be rounding differences).
* Yearly staking return: Estimate annual return: daily \* 365.

The chart below the graph calculates staking returns for all validators: 

<Image align="center" src="https://files.readme.io/92e9cf2-Screenshot_2024-06-24_at_11.18.44.jpg" />

<br />

# The Math

All values are calculated with the nominator/24hours/1000 tao value.  This is calculated over a 30 day moving average.  We use a moving average to "smooth out" large changes in delegation that would provide inaccurate return values.

This also means that changes in "Take" will take time to significantly change the returns in the chart.

> 🚧 Read carefully the caveats of the calculator. These are estimates, based on overall network averages, and not actual validator returns.  It also does not account for compounding or changes in tao valuation.

# Why is the staking APR declining?

Let's say that the daily total distributed to stakeholders is 3,000 tao.  If there is 6M tao staked, this will be distributed evenly:

<Image align="center" src="https://files.readme.io/b15a31f-Screenshot_2024-06-25_at_11.05.30.jpg" />

As more tao is staked, the denominator gets larger, but the numerator stays constant.

![](https://files.readme.io/81b32c3-image.png)

As more and more tao is staked, the amount of tao earned decreases - decreasing the APY.
