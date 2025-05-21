---
title: Miner (Architecture)
excerpt: >-
  Miners are nodes in a Bittensor subnet that produce output as defined by the
  subnet code.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
> 📘 This section focuses on the miner architecture inside a subnet.
> 
> The [Miner persona](doc:miner) has details on how a miner can be run.

Miners produce output as defined by the subnet code. As miners are only scored by validators and there is no incentive for them to receive or trust requests from anyone else, all requests to the miners pass through a validator.

![](https://files.readme.io/7f1f48b-image.png)

# Hardware requirements

Mining hardware requirements vary by subnet although most require some for of GPU to perform the require compute functions.  Each subnet's github repository should have a `min_compute.yml` or information in the readme, describing the hardware requirements for mining the subnet. See: [Bittensor Subnets](doc:list-of-subnets-1) for links.

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2F3pfPUFxhprY%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3D3pfPUFxhprY&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2F3pfPUFxhprY%2Fhqdefault.jpg&key=7788cb384c9f4d5dbbdbeffd9fe4b92f&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen; encrypted-media; picture-in-picture;\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=3pfPUFxhprY",
  "title": "Introduction to Mining on Bittensor",
  "favicon": "https://www.google.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/3pfPUFxhprY/hqdefault.jpg",
  "provider": "https://www.youtube.com/",
  "href": "https://www.youtube.com/watch?v=3pfPUFxhprY",
  "typeOfEmbed": "youtube"
}
[/block]


<br>

# Miner Trust/Incentive

Each miner works to maximise their trust and incentive metrics on the network. This is done by meeting the validation requirements for the subnet at a higher level than their peers.  Each validator will grade the results of the miner, assigning a score.  Each epoch, the incentive scores (weights) are aggregated by the consensus mechanism to determine the miner's emissions.

See [Incentive for Miners](doc:consensus-for-miners) for a detailed breakdown of how minder incentive is calculated.

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FZ2s7jEJK_m4&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DZ2s7jEJK_m4&image=http%3A%2F%2Fi.ytimg.com%2Fvi%2FZ2s7jEJK_m4%2Fhqdefault.jpg&key=7788cb384c9f4d5dbbdbeffd9fe4b92f&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen; encrypted-media; picture-in-picture;\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=Z2s7jEJK_m4",
  "favicon": "https://www.google.com/favicon.ico",
  "image": "http://i.ytimg.com/vi/Z2s7jEJK_m4/hqdefault.jpg",
  "provider": "http://youtube.com",
  "href": "https://www.youtube.com/watch?v=Z2s7jEJK_m4",
  "typeOfEmbed": "youtube"
}
[/block]


<br>

# Miner Registration

Learn how to [register a node](doc:node-registration) on a subnet.