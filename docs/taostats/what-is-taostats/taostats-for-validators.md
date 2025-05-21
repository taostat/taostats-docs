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

* **Stake**: A yellow stake indicates that there are parent hotkeys adding stake to this validator. (see [Child Hotkeys](doc:child-hotkeys))
* **VTrust**: Indication of how well the validator is "in consensus" with the other validators.
* **Updated**: Number of blocks since the validator last placed weights. Should always be around 100, but never over 1,000.
* **Dividends**: Dividends in a subnet add to 1 for all validators. The emission share to validators is multiplied times dividends to determine the validator's emission.

![](https://files.readme.io/345829ae32e6c7dd7c4c911e311d732e2f2ff541e2237ff131a55e2523471e42-image.png)

<br />

# Explorer

Each validator has an explorer page [https://x.taostats.io/validator/](https://x.taostats.io/validator/)&lt;hotkey&gt;. There are a number of views to understand validator success on this page:

## Summary information

The top of the explorer page has basic data on the validator - amount staked, Dominance (% of network stake) and daily returns.

<Image align="center" src="https://files.readme.io/c12f1a8-Screenshot_2024-06-10_at_11.25.21.jpg" />

<br />

## Staked

A chart showing a historical review of tao staked (blue) and number of nominators (orange):

<Image align="center" src="https://files.readme.io/5d38f7a-Screenshot_2024-06-10_at_11.17.20.jpg" />

## Performance

The performance tab has a box for each subnet you are actively validating on:

![](https://files.readme.io/fddd25e96b33d8fa896544e955f5777afeca8ac951a31a8e244a2f07b0720cfe-image.png)

<br />

* Dividends will turn red if the number falls below the dominance (% to total stake). This indicates that your emissions are lower than they should be on a particular subnet.
* Updated will turn red if the number is &gt; 100 - as dividends begin to drop if weights are not set every 100 blocks.

<Image align="center" src="https://files.readme.io/d844fdb79794e568ee02716b4214df5ab1431c63a5a9c02aa981899d9dbe6e88-Screenshot_2024-09-06_at_14.54.13.jpg" />

## Updated

The number of blocks emitted since your validator last updated miner scores. This number should stay under 100. As the number gets further from 100, your Vtrust will be reduced - as your validator is no longer placing weights on the miners.

Click #performance on the validator page. Each subnet will have an udpated number, and a chart below the blocks showing historical data:

<Image align="center" src="https://files.readme.io/cf726f8d64430efd0f5ed472ba9df66a855939c6955b09d4a390c027521727b5-Screenshot_2024-09-06_at_14.54.33.jpg" />

<br />

## VTrust

Validator trust. Scored based on the weighting the validators give to the miners, and the Updated number. Higher Vtrust is desired, as a high Vtrust ensures higher emissions. Vtrust is reduced when the validator is out of consensus with other validators, or when miner weights have not been set often enough.

## Stake

Keeping track of the stake delegated to your validator is important as this has a large weight on your emission percentage (referred to as *dominance* above). The chart shows the number of nominators (wallets that have delegated) in orange and the total stake in blue.

<Image align="center" src="https://files.readme.io/a723c2a158010f633c74ba846767a20a288520546a4895afe42ad93d5f07a265-Screenshot_2024-09-06_at_14.55.11.jpg" />

> 📘 Note that the stake directly held by the validator and the stake on the subnet can vary.
>
> ![](https://files.readme.io/cad3f669d261ffa2db63ff43d98ea6392684a9a47665f5d3761e66a54680918e-image.png)
>
> Taostats has a stake of 822k.
>
> But on subnet 19, there are 3 parent hotkeys delegating tao to Taostats - adding another 341k stake on this subnet.
>
> Similarly, Datura has 549k tao, but on Subnet 19, it shows much less than that - it has delegated 300k tao to various child hotkeys (taostats included).

<br />

# Dividends

This is the percentage of Validator emissions that is allocated to your validator. If your validator is healthy and has a good Vtrust - the Dividend should be close to the dominance.

<br />

# Take

Validator emissions are divided amongst the validator and the delegates. The validator receives a commission % of emissions called `take`. This is set on the network once every 30 days and ranges from 0-18%.

<br />

The remainder of the emission is awarded to the delegates, based on a weighted average.