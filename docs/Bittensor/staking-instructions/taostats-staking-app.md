---
title: Taostats Staking App
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
The [Taostats Staking App](https://dash.taostats.io/stake) is part of the taostats dashboard. There are a few options to stake here:

* ## Simple
* ## Manual
* ## [Balance](#Balance)

<br />

# Balance

<Embed url="https://www.youtube.com/watch?v=8Kjjefp5mK4" href="https://www.youtube.com/watch?v=8Kjjefp5mK4" typeOfEmbed="youtube" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252F8Kjjefp5mK4%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253D8Kjjefp5mK4%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252F8Kjjefp5mK4%252Fhqdefault.jpg%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" />

> 📘 Undelegating & Unstaking - negative stake is removing stake from that validator.

# Staking Dashboard

Once you have [Connected your wallet](doc:connecting-your-wallet): you will see a staking page:

![](https://files.readme.io/031574325d641374cb98d18fcd1060caf6f2079605973eeafcff9a3a432f4ac0-image.png)

## Tao overview

Select how much tao you have set available to delegate. In this screenshot 27.47 tao is delegated of 31.13 total tao (88.58%)

![](https://files.readme.io/12661fd8ba15084e98afdd2f22fb33683721d6a3760774bff151ddb553708c6c-image.png)

Moving the slider to the left will reduce the amount of tao being staked. Moving to the right will add more tao to be staked.

## Slippage

![](https://files.readme.io/1458c923d7e75ba9b84186769fb76d6eeb658c23b9d9c1aa62df0b644d62e2f1-image.png)

Set the Max Slippage you are comfortable with having on any Stake event.

## Stakes

![](https://files.readme.io/30ff3bb1b2767f9bdae5546a9208ef427779a706b96b3cb909dfcb79783603c2-image.png)

This screenshot is from testnet, so the validator name is "Unknown."

Moving the sliders will chnage the staking for all subnets.  The Lock prevents a stake from changing.

### Example

In the screenshot the amount of stake from SN1 drops from 25 tao to 12 tao. The other subnet's stake grows proportionally. Note that SN19 has 1.55% slippage, which is over the Max Slippage value, and appears in red.

![](https://files.readme.io/10410fc47b9fe0330d5487c1e3355f8697893bdf03cad4ad114701b1498f9440-image.png)

<br />

## Fees

Every staking and unstaking action on the chain costs 50,000 rao (0.00005 tao). This is rounded to zero in the taostats view:

![](https://files.readme.io/f4bdcd8efa78ac0374e4b4b9b460f329446e3e2a21eb32a48bd9ff0d61a3f96b-image.png)

<br />

### Multiple transactions

<br />

If there are multiple actions - this fee is assessed for each action.

All of the actions are run inside a batch command, which is also assessed a fee on chain:

![](https://files.readme.io/5528e72218f1017903e4f9ae7e4579921b408fe7e278bd9dc4b8dd640c5f78b8-image.png)

Once the change has been made, the final fee can be seen in the Extrinsic:

![](https://files.readme.io/c72e861a99dc4061f1a2b53515a7011a9132c0af2defac57174eefcc97c729ba-image.png)

> 📘 These are chain fees. Taostats does not charge for staking or unstaking.

# [Stake troubleshooting](doc:stake-troubleshooting)