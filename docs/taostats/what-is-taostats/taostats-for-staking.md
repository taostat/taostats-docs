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

Validators that have verified are listed on Taostats <https://taostats.io/verified-validators/>.

Learn about the validators, and how they are contributing to the Bittensor network. By staking with a validator, you are supporting this work.  The table shows the amount of tao that is delegated to them, and the % of network delegated tao:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/651eec5-image.png",
        null,
        "Taostats validator as of Feb. 5 2024."
      ],
      "align": "center",
      "caption": "Taostats validator as of Feb. 5 2024. The Taostats team think this is a great choice for staking."
    }
  ]
}
[/block]


The info button takes you to the [validator explorer](https://docs.taostats.io/docs/taostats-for-validators#explorer)  page, providing details about the validator's performance.   

<br />

## Return on your stake

When you stake your TAO on a validator, you'll want an idea of the amount of emissions you will receive. Taostats has a _very basic_ calculator that uses the average emissions across the entire bittensor network: <https://taostats.io/staking/>. 

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FGzB381fBQQM%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DGzB381fBQQM&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FGzB381fBQQM%2Fhqdefault.jpg&key=7788cb384c9f4d5dbbdbeffd9fe4b92f&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen; encrypted-media; picture-in-picture;\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=GzB381fBQQM",
  "title": "Bittensor Delegation: How are your rewards calculated",
  "favicon": "https://www.google.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/GzB381fBQQM/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=GzB381fBQQM",
  "typeOfEmbed": "youtube"
}
[/block]


<br />

To compare the returns of each validator, visit: <https://x.taostats.io/validators>. There are two values to be aware of:

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
> > 📘 [block:image]{"images":[{"image":["https://files.readme.io/e360a53-image.png",null,""],"align":"center","sizing":"24% "}]}[/block]
> 
> This change occurred as ~1/2 of their delegation was removed.  If the actual numbers were 500k staked resulting in 50tao created - all of a sudden the math is showing 50tao created on 250k staked - and the metric appears to be double the actual number.  With the lower stake, the tao emitted was much less, and the value returned to the previous value in about 24 hours.

## NOM/24hr/1ktao and APY

How do APY and NOM/24hr/1k TAO relate?  Here is a chart based on May 1, 2024 data, including a take percentage:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/331e0ff-image.png",
        null,
        ""
      ],
      "align": "center",
      "sizing": "75% "
    }
  ]
}
[/block]