---
title: 'Taostats: For Validators'
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
# Metagraph

In the metagraph, there are several columns that a validator must constantly track:

- Stake:
- VTrust
- Updated
- Dividends

# Explorer

Each validator has an explorer page <https://x.taostats.io/validator/><hotkey>. There are a number of views to understand validator success on this page:

## Summary information

The top of the explorer page has basic data on the validator - amount staked, Dominance (% of network stake) and daily returns.

![](https://files.readme.io/ff90560-image.png)

<br />

## Staked

A chart showing a historical review of tao staked (blue) and number of nominators (orange):

![](https://files.readme.io/6056420-image.png)

## Performance

The performance tab has a box for each subnet you are actively validating on.  

- Dividends will turn red if the number falls below the dominance (% to total stake).  This indicates that your emissions are lower than they should be on a particular subnet.  
- Updated will turn red if the number is > 100 - as dividends begin to drop if weights are not set every 100 blocks.

![](https://files.readme.io/6d604c1-image.png)

## Updated

The number of blocks emitted since your validator last updated miner scores. This number should stay under 100. As the number gets further from 100, your Vtrust will be reduced - as your validator is no longer placing weights on the miners.

Click #performance on the validator page. Each subnet will have an udpated number, and a chart below the blocks showing historical data:

![](https://files.readme.io/4b0ca2f-image.png)

<br />

## VTrust

Validator trust.  Scored based on the weighting the validators give to the miners, and the Updated number.  Higher Vtrust is desired, as a high Vtrust ensures higher emissions.  Vtrust is reduced when the validator is out of consensus with other validators, or when miner weights have not been set often enough.

## Stake

Keeping track of the stake delegated to your validator is important as this has a large weight on your emission percentage (referred to as _dominance_ above). The chart shows the number of nominators (wallets that have delegated) in orange and the total stake in blue.

![](https://files.readme.io/f0dc99c-image.png)

<br />

# Dividends

This is the percentage of Validator emissions that is allocated to your validator.  If your validator is healthy and has a good Vtrust - the Dividend should be close to the dominance.

<br />

# Take

Validator emissions are divided amongst the validator and the delegates.  The validator receives a commission % of emissions called`take`.  This is set on the network once every 30 days and ranges from 9-18%.  

<br />

The remainder of the emission is awarded to the delegates, based on a weighted average.