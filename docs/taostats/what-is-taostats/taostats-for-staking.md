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

# Staking

Staking is the process of delegating your tao to a validator.  Validators with more delegated stake receive greater emissions.  You can also choose to support validators who work towards building the Bittensor ecosystem (with higher emissions, validators earn more tao, so by supporting validators who work on the ecosystem, you support their work.)

## Staking hold period

Each hotkey/coldkey pair can make **one** stake/unstake transaction per epoch (360 blocks or approximately 72 minutes).

> 📘 You can delegate your tao on [taostats](https://delegate.taostats.io/), or use the [Bittensor CLI](doc:cli-stake) to stake tao.

## Choosing a validator

Validators that have verified are listed on Taostats [https://taostats.io/verified-validators/](https://taostats.io/verified-validators/).

Learn about the validators, and how they are contributing to the Bittensor network. By staking with a validator, you are supporting this work.  The table shows the amount of tao that is delegated to them, and the % of network delegated tao:

<Image alt="Taostats validator as of Feb. 5 2024." align="center" src="https://files.readme.io/651eec5-image.png">
  Taostats validator as of Feb. 5 2024. The Taostats team think this is a great choice for staking.
</Image>

The info button takes you to the [validator explorer](https://docs.taostats.io/docs/taostats-for-validators#explorer)  page, providing details about the validator's performance.   

<br />

## Return on your stake

When you stake your TAO on a validator, you'll want an idea of the amount of emissions you will receive. Taostats has a *very basic* calculator that uses the average emissions across the entire bittensor network: [https://taostats.io/staking/](https://taostats.io/staking/). 

<Embed url="https://www.youtube.com/watch?v=GzB381fBQQM" title="Bittensor Delegation: How are your rewards calculated" favicon="https://www.google.com/favicon.ico" image="https://i.ytimg.com/vi/GzB381fBQQM/hqdefault.jpg" provider="youtube.com" href="https://www.youtube.com/watch?v=GzB381fBQQM" typeOfEmbed="youtube" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252FGzB381fBQQM%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253DGzB381fBQQM%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252FGzB381fBQQM%252Fhqdefault.jpg%26key%3D7788cb384c9f4d5dbbdbeffd9fe4b92f%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" />

<br />

To compare the returns of each validator, visit: [https://x.taostats.io/validators](https://x.taostats.io/validators). There are two values to be aware of:

# Take

Validator emission is divided amongst all of those who delegate.  The validator can take a small percentage of the emissions.  This is default set at 18%, but can range from 9-18%.  

> 📘 How does `take` affect my return?
>
> A rough APY for the bittensor network as a whole:
>
> 0% take:  18.3% APY
>
> 10% take: 16.9% APY
>
> 18% take: 15.5% APY

# NOM/24hr/1ktao

> 😀 What is NOM/24hr/1k tao?
>
> This is the emission delivered by the validator over the last 24 hours for 1,000 tao. If you were to stake 1,000 tao, your account would receive this much tao every 24 hours (it is a running average, and numbers fluctuate, but it will be close to this value.)

> 📘 If it looks fishy - maybe it is.
>
> Calculation of NOM/24h/1ktao is a real time calculation, and fluctuations in the amount staked can greatly influence the value.  If you see a validator that is showing an extremely high value - dig into the numbers to see that it is accurate. In the screenshot below, one validator appears to have twice the return of all the others - for about 24 hours, before it settled back.
>
> > 📘 <Image align="center" width="24% " src="https://files.readme.io/e360a53-image.png" />
>
> This change occurred as \~1/2 of their delegation was removed.  If the actual numbers were 500k staked resulting in 50tao created - all of a sudden the math is showing 50tao created on 250k staked - and the metric appears to be double the actual number.  With the lower stake, the tao emitted was much less, and the value returned to the previous value in about 24 hours.

## NOM/24hr/1ktao and APY

How do APY and NOM/24hr/1k TAO relate?  Here is a chart based on May 1, 2024 data, including a take percentage:

<Image align="center" width="75% " src="https://files.readme.io/331e0ff-image.png" />
