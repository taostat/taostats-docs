---
title: Tao Allocation
excerpt: ''
deprecated: true
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

* root validators assigning weights (value) to each subnet. 
* The amount of alpha staked on  each subnet

These are allocated in the [Root Subnet](doc:root-subnet), and [Yuma Consensus](doc:consensus) determines the % allocation for each subnet through a consensus mechanism across all validators with a weighting prioritisation based on total stake by a given validator.

This means that validators with larger delegated stake have a greater responsibility and influence on the value assigned to subnets and network participants. There is an active discussion/proposal to shift this mechanism towards a more dynamic market led solution (Dynamic Tao) however this proposal is still being tested and has not yet been deployed.

The emitted tao is split based on individual subnet emissions:

<Image alt="An example subnet distribution (captured Feb. 8, 2024)." align="center" width="50% " src="https://files.readme.io/73ae93e-image.png">
  An example subnet distribution (captured Feb. 8, 2024).
</Image>

As subnets become more and more competitive, it is expected that the allocations will become evenly distributed, closer to a 3.1% mean for each subnet with variance towards those that are perceived or proved to provide greater value to the network.

> 📘 Subnet 18 has an allocation of 10%.
>
> For each tao emitted by the blockchain, subnet 18 will receive 0.10 tao.

<br />

## Tao Allocation to the root subnet

 Tao emissions to the root subnet are recycled. See [Root Subnet](doc:root-subnet) for more details.

# Subnet division

For each subnet allocation, the tao is further divided amongst the Subnet owner, the validators and the miners.  After the subnet owners commission, the remainder is split 50:50 between validators and miners.

* Subnet owner: 18%
* Validators 41%
* Miners 41%

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

<Embed url="https://www.youtube.com/watch?v=GDyqOB7hDNM" title="Bittensor Emissions: Miner deep dive" favicon="http://www.google.com/favicon.ico" image="https://i.ytimg.com/vi/GDyqOB7hDNM/hqdefault.jpg" provider="youtube.com" href="https://www.youtube.com/watch?v=GDyqOB7hDNM" typeOfEmbed="youtube" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252FGDyqOB7hDNM%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253DGDyqOB7hDNM%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252FGDyqOB7hDNM%252Fhqdefault.jpg%26key%3D7788cb384c9f4d5dbbdbeffd9fe4b92f%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" />

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

<Image alt="Here are two validators: one has a take of 18%, the other 9%." align="center" src="https://files.readme.io/308269f-image.png">
  Here are two validators: one has a take of 18%, the other 9%.
</Image>

> 📘 The top validator has 1,206,944 tao
>
> The top (fictional) stakeholders are shown below. (note that take is hardcoded at 18%).
>
> ![](https://files.readme.io/1a19485-image.png)
>
> If stakeholder 1 has 120k tao, they hold 10% of the total stake.  Each epoch, their fraction is 0.348 tao. They receive 82% after the validator's take, and receive 0.2855 tao in the epoch.

<Embed url="https://www.youtube.com/watch?v=jS-1m1OaCn8" title="Bittensor Emissions: Deep Dive for Validators and Delegates" favicon="https://www.google.com/favicon.ico" image="https://i.ytimg.com/vi/jS-1m1OaCn8/hqdefault.jpg" provider="youtube.com" href="https://www.youtube.com/watch?v=jS-1m1OaCn8" typeOfEmbed="youtube" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252FjS-1m1OaCn8%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253DjS-1m1OaCn8%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252FjS-1m1OaCn8%252Fhqdefault.jpg%26key%3D7788cb384c9f4d5dbbdbeffd9fe4b92f%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" />

## Using Delegation Calculators

<br />

<Embed url="https://www.youtube.com/watch?v=GzB381fBQQM" title="Bittensor Delegation: How are your rewards calculated" favicon="https://www.google.com/favicon.ico" image="https://i.ytimg.com/vi/GzB381fBQQM/hqdefault.jpg" provider="youtube.com" href="https://www.youtube.com/watch?v=GzB381fBQQM" typeOfEmbed="youtube" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252FGzB381fBQQM%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253DGzB381fBQQM%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252FGzB381fBQQM%252Fhqdefault.jpg%26key%3D7788cb384c9f4d5dbbdbeffd9fe4b92f%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" />

<br />

# dtao

Dtao is a proposal that will upend much of the tao allocation.  Pages on Dtao are coming soon.