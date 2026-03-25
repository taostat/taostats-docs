---
title: Staking
excerpt: Staking tao/alpha is how investors earn yield.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
<Callout icon="📘" theme="info">
  # Staking with taostats

  See [Staking Instructions](doc:staking-instructions) for a number of pages describing how to stake using Taostats.
</Callout>

<br />

Staking plays a principal role in the functioning of the Bittensor network. In February 2025, the dTao release gave stakeholders additional power: staking into a subnet increases the emissions of the subnet.

# Staking Options

in dTao, there are two options for staking:

* [Staking to root](#staking-to-root)
* [Staking to a Subnet](#staking-to-alpha)

<br />

# Staking to root

Staking to root uses only tao.  Your tao is staked on a root validator, and you receive returns based on the validator's performance in the subnets.

Staking to root is a `safe`  staking option - there is no way to lose tao value.  However, root staking decreases over time [by design](doc:stakeholder-emissions-root-vs-alpha), as the root proportion decreases on all subnets.

<RootProp />

Emission is rewarded approximately every 2 days.  But it is randomly awarded by the chain, and a week is not abnormal.

<Callout icon="📘" theme="info">
  Auto Claim vs. Manual Claim

  You can manually claim your root rewards, if you feel that the auto claim is taking too long.  Our analysis shows that the *extrinsic fee* you pay for the manual claim often EXCEEDS the amount or reward you have earned.  You can actually lose tao value doing this.

  ![](https://files.readme.io/0f13dd72cfd0cc430c7f18f95f32a3868968f2ed36a4177474d1966d075eac34-image.png)

  https://x.com/dougsillars/status/2033580026134777960
</Callout>

<Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=Ed7SCDGmM4Q" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252FEd7SCDGmM4Q%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253DEd7SCDGmM4Q%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252FEd7SCDGmM4Q%252Fhqdefault.jpg%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" href="https://www.youtube.com/watch?v=Ed7SCDGmM4Q" providerUrl="https://www.youtube.com/" providerName="YouTube" />

<br />

## Root Staking Options

In November 2025, Bittensor launched the following change to the way root stake operates:

Emissions are not automatically awarded every 360 blocks, but will be awarded approximately daily.  The time will be random, and so may be sometimes longer than a day, sometimes less than a day.

Stakeholders will have two options in receiving rewards:

### (Default) Swap (root claim)

Root claim is the default option, and works similarly to the way root sketig works today. All the alpha earned will be converted to tao, and awarded to your root hotkey, approximately once a day.

### Keep (Alpha Claim)

In fall 2025, root stakeholders may choose alpha claim.  This feature keeps your earned emission in alpha in every subnet.  In this scenario, the claimed alpha is _not_ converted to tao, but remains on the subnet staked as alpha.

### Keep Selected

This is a hybrid - you can choose to keep alpha for some subnets. The remaining subnets will be sold to tao, and your root balance will be increased.

# Staking to alpha

This is the new feature and primary goal of dTao - to enable stakeholders to vote and determine the emissions for every subnet.

To stake in alpha, tao is exchanged via the [Subnet Pools](doc:subnet-pools) into alpha.  This will incur [Slippage](doc:slippage). The received alpha is then staked to the validator selected.  Your returns will be in alpha, and autocompounded to the validator hotkey.

Staking to alpha _does_ incur risk: a drop in alpha token price will result in a lower amout of tao when unstaking.

Emission is awarded every 360 blocks (approx 72 minutes).

> 📘 Staking fees
>
> For all staking transactions, there is a small extrinsic fee charged.  Taostats currently does not allow staking without leaving a small amount of tao fee to pay for the unstaking transaction.
>
> ## Root
>
> There is no fee to stake or unstake from root
>
> ## Subnets:
>
> * All staking and unstaking fees are default 0.05% of the stake/unstake value.
> * Note that this can be changed by the subnet owner.
>
> ## Get the current fee for a subnet
>
> <StakingFee2 />

<br />

## Moving stake

The move stake command can be used to switch validators in a subnet.  Under the hood, this is an unstake, and then staking.  However, only one fee is charged.

<br />

## [dTao FAQ](doc:dtao-faq): Your top  staking questions

<br />

<br />
