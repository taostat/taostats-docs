---
title: Tao Allocation
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Every time a block is added to the chain, 1 tao is created.  This tao is then distributed amongst the subnet pools.

# Subnets

The allocation for each subnet is defined by two actions:

- root validators assigning weights (value) to each subnet. 
- The amount of alpha staked on  each subnet

These are allocated in the [Root Subnet](doc:root-subnet), and [Yuma Consensus](doc:consensus) determines the % allocation for each subnet through a consensus mechanism across all validators with a weighting prioritisation based on total stake by a given validator.

This means that validators with larger delegated stake have a greater responsibility and influence on the value assigned to subnets and network participants. There is an active discussion/proposal to shift this mechanism towards a more dynamic market led solution (Dynamic Tao) however this proposal is still being tested and has not yet been deployed.

The emitted tao is split based on individual subnet emissions:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/73ae93e-image.png",
        null,
        "An example subnet distribution (captured Feb. 8, 2024)."
      ],
      "align": "center",
      "sizing": "50% ",
      "caption": "An example subnet distribution (captured Feb. 8, 2024)."
    }
  ]
}
[/block]


As subnets become more and more competitive, it is expected that the allocations will become evenly distributed, closer to a 3.1% mean for each subnet with variance towards those that are perceived or proved to provide greater value to the network.

> 📘 Subnet 18 has an allocation of 10%.
> 
> For each tao emitted by the blockchain, subnet 18 will receive 0.10 tao.

<br />

## Tao Allocation to the root subnet

 Tao emissions to the root subnet are recycled. See [Root Subnet](doc:root-subnet) for more details.

# Subnet division

For each subnet allocation, the tao is further divided amongst the Subnet owner, the validators and the miners.  After the subnet owners commission, the remainder is split 50:50 between validators and miners.

- Subnet owner: 18%
- Validators 41%
- Miners 41%

Although these proportions are not variable, it should be noted that they could and likely will be adjusted in the future to adapt with the network state and assure continued stability and sustainability. For example it is generally accepted that validators should be building revenue generating business models on the network and that the 50:50 split would likely weight more towards miners as the network matures.

> 📘 Subnet 8 receives 0.10 tao
> 
> ![](https://files.readme.io/a160252-image.png)
> 
> The subnet owner receives 0.018 tao, and the miners and validators each are awarded 0.041 tao.

# Miner allocation

Each subnet has a number of miners - generally just over 200.  To divide the Miner allocation of tao, [Yuma Consensus](doc:consensus) uses the Trust value (provided by the subnet's validators) to determine Incentive.  Incentive is the percentage of the tao awarded to each miner.

> 📘 The Miner allocation is 0.041
> 
> Here is a sample breakdown for the top four miners in the subnet:
> 
> The tao awarded to each miner is 0.041 x incentive.
> 
> In the [taostats](https://taostats.io) metagraph, emission is displayed.  Emission is tao/epoch. 
> 
> With 360 blocks/epoch, take the tao column below  x 360 to obtain emission.
> 
> ![](https://files.readme.io/f260797-image.png)

<br />

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FGDyqOB7hDNM%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DGDyqOB7hDNM&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FGDyqOB7hDNM%2Fhqdefault.jpg&key=7788cb384c9f4d5dbbdbeffd9fe4b92f&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen; encrypted-media; picture-in-picture;\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=GDyqOB7hDNM",
  "title": "Bittensor Emissions: Miner deep dive",
  "favicon": "http://www.google.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/GDyqOB7hDNM/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=GDyqOB7hDNM",
  "typeOfEmbed": "youtube"
}
[/block]


# Validator allocation

The validator emission is divided amongst the validators based on the vtrust calculated by [Yuma Consensus](doc:consensus) and weighted by the amount of delegated stake to the validator.  This is used to calculate the dividends column, a percentage of the validator allocation awarded to the validators.

> 📘 The Validator allocation is 0.041
> 
> Stake and vtrust are used to calculate the dividend value (the percentage of the tao to be awarded to each validator).  Dividend x (validator tao) = invividual validator reward.
> 
> In the [taostats](https://taostats.io) metagraph, the emission value is displayed.  Emission is tao/epoch (360x the tao value).
> 
> ![](https://files.readme.io/61b1304-image.png)

# Delegation/Staking rewards

Validators do not receive 100% of the emissions awarded to them. As their emission is proportional to the stake/delegation granted to the validator, most of the emissions are further divided amongst the delegates who have staked tao with the validator.  The validator is awarded a percentage of the emissions - called Take.  The take value is a variable that can be set by the validators once every 30 days and ranges from 9-18%. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/308269f-image.png",
        null,
        "Here are two validators: one has a take of 18%, the other 9%."
      ],
      "align": "center",
      "caption": "Here are two validators: one has a take of 18%, the other 9%."
    }
  ]
}
[/block]


> 📘 The top validator has 1,206,944 tao
> 
> The top (fictional) stakeholders are shown below. (note that take is hardcoded at 18%).
> 
> ![](https://files.readme.io/1a19485-image.png)
> 
> If stakeholder 1 has 120k tao, they hold 10% of the total stake.  Each epoch, their fraction is 0.348 tao. They receive 82% after the validator's take, and receive 0.2855 tao in the epoch.

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FjS-1m1OaCn8%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DjS-1m1OaCn8&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FjS-1m1OaCn8%2Fhqdefault.jpg&key=7788cb384c9f4d5dbbdbeffd9fe4b92f&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen; encrypted-media; picture-in-picture;\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=jS-1m1OaCn8",
  "title": "Bittensor Emissions: Deep Dive for Validators and Delegates",
  "favicon": "https://www.google.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/jS-1m1OaCn8/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=jS-1m1OaCn8",
  "typeOfEmbed": "youtube"
}
[/block]


## Using Delegation Calculators

<br />

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

# dtao

Dtao is a proposal that will upend much of the tao allocation.  Pages on Dtao are coming soon.