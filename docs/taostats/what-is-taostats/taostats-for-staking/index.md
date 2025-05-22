---
title: 'Taostats: For Staking'
excerpt: Understand how to read the data in order to stake your tao
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Staking is a great option if you want to support the Bittensor network with tao, but do not want to run a subnet or neuron.

> 📘 [Staking Instructions](doc:staking-instructions) - Use taostats for all your staking transactions!

# Staking

Staking is the process of delegating your tao to a validator.

## Root stake

Validators with high VTrust across as many subnets as possible will have the highest root returns.  You can also choose to support validators who work towards building the Bittensor ecosystem (with higher emissions, validators earn more tao, so by supporting validators who work on the ecosystem, you support their work.)

## Alpha Stake

Staking in a subnet involves buying an alpha token.  See [Staking in dTao](doc:staking-in-dtao) for full details. Your staked alpha will always increase.  However, the exchange rate between tao/alpha may change - leading to a net loss of funds.

<br />

<br />

## Staking hold period

There is no hold period for staking.

## Staking Risk

* **Root**: There is no risk to staking on root Bittensor. Your staked tao is on a hotkey, but it never leaves your wallet.
* **Alpha**: When buying alpha, you are purchasing a new token. Your alpha stake will always increase, but the price of alpha/tao will fluctuate. This can lead to a loss in funds.

## Choosing a validator

Learn about the validators, and how they are contributing to the Bittensor network. By staking with a validator, you are supporting this work.  The table shows the amount of tao that is delegated to them, and the % of network delegated tao:

<Image align="center" alt="Taostats validator as of Feb. 5 2024." border={false} caption="Taostats validator as of Feb. 5 2024. The Taostats team think this is a great choice for staking." src="https://files.readme.io/e48533f5d1fa91b79717f10261f9438c8729bcc6120261d6d03859941eb18469-Screenshot_2024-09-06_at_14.53.04.jpg" />

The info button takes you to the [validator explorer](https://docs.taostats.io/docs/taostats-for-validators#explorer)  page, providing details about the validator's performance.

<br />

## Return on your stake

When you stake your TAO on a validator, you'll want an idea of the amount of emissions you will receive. Taostats has a *very basic* calculator that uses the average emissions across the entire bittensor network: [https://taostats.io/staking/](https://taostats.io/staking/).

<Embed url="https://www.youtube.com/watch?v=GzB381fBQQM" href="https://www.youtube.com/watch?v=GzB381fBQQM" typeOfEmbed="youtube" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252FGzB381fBQQM%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253DGzB381fBQQM%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252FGzB381fBQQM%252Fhqdefault.jpg%26key%3D7788cb384c9f4d5dbbdbeffd9fe4b92f%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" />

<br />

# APY

[https://taostats.io/yield](https://taostats.io/yield) displays the APY for all subnets including root

![](https://files.readme.io/782e22a0a839ab3960a62e80624c947b0db391a2194d403f43d9e1635cb99f00-image.png)

This page is calculated based on **actual returns** over the period.  As always *past performance does not indicate future gains*.

Root APY will be in decline as subnets mature, due to [Emissions: Root vs. Alpha Stake](doc:stakeholder-emissions-root-vs-alpha).