---
title: Subnet Emissions
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
1 tao is minted for each block that is created in the Bittensor blockchain (this occurs every 12 seconds). This emission is divided amongst the subnets based on weights set by validators in Subnet 0.

## Calculating Subnet Emissions

Subnet weights are defined in the [Root Subnet](doc:root-subnet) by validators using the cli command `btcli r weights`.  Validators can set a score for any or all subnets and their submitted scores are normalised to equal a total of 1.0 (100%). Here is an example screenshot from Taostats for the top 3 validators (based on stake):

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a834e163322a78a1dec9e6638b3fe9b0778ba9502a44f137ce25c9c8504089ce-Screenshot_2024-09-03_at_17.39.21.jpg",
        null,
        "This chart can be found on the landing page: <https://taostats.io/>"
      ],
      "align": "center",
      "caption": "This chart can be found on the landing page: [taostats.io](https://taostats.io/)"
    }
  ]
}
[/block]


In this screenshot, the top validator ranks subnet 1 at 3.02%, and validator 2 ranks subnet 1 at 4%. The values allocated across the subnets by each validator will always add up to 1.0 (100%).   

To calculate the total emissions Yuma Consensus takes into account both the score, the weight of the validator based on their stake and the consensus amongst the other validators weights to finalise the distribution of emissions across all subnets.  The distribution percentage for each subnet is shown across the header of the table.

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2Fm1QvCtfzHm0%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3Dm1QvCtfzHm0&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2Fm1QvCtfzHm0%2Fhqdefault.jpg&key=7788cb384c9f4d5dbbdbeffd9fe4b92f&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen; encrypted-media; picture-in-picture;\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=m1QvCtfzHm0",
  "title": "Bittensor Emissions deep-dive: Subnet emissions distribution",
  "favicon": "https://www.google.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/m1QvCtfzHm0/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=m1QvCtfzHm0",
  "typeOfEmbed": "youtube"
}
[/block]


<br />

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c5f341d4a2c36865c6b0d2c06d3516ff9735ea2958695ed04949ec586657d00a-image.png",
        null,
        "The distribution of emission to the top 11 Subnets."
      ],
      "align": "center",
      "caption": "The distribution of emission to the top 11 Subnets."
    }
  ]
}
[/block]


<br />

## Subnet Emission Distribution

Each subnet's incentive mechanism breaks down the distribution of the Subnet's share of emissions to the active participants of the subnet.

- **Subnet Owner**: The subnet owner receives 18% of the emissions. 
- **Miner** Miners split 41% of emissions. 
- **Validator** Validators also split 41% of emissions. 

**Miners** are awarded emissions based on their emissions. Emissions are granted to each miner by validators, based on their incentive score derived from the quality of their work.  The evaluation criteria is set by the subnet incentive mechanism. See [Incentive for Miners](doc:consensus-for-miners) for more detail on how incentive is awarded to miners.

**Validators** are awarded emissions based on the amount of tao they have staked, and the performance and consensus with other validators on the network, represented by the vtrust metric. See [Incentive for Validators](doc:incentive-for-validators) for more detail on how incentive is awarded to validators.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/14578d321b33b4d9a6d1de35af5acb919f4baee021c16faad77d059f0f351817-image.png",
        null,
        "Emission breakdown of Subnet 19: 18% to owner, 41% to Miners & Validators."
      ],
      "align": "center",
      "caption": "Emission breakdown of Subnet 19: 18% to owner, 41% to Miners & Validators."
    }
  ]
}
[/block]