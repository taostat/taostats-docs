---
title: Running a Miner
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
A miner deploys (at least) one mining node into (at least) one subnet to perform the work being rewarded by the subnet incentive mechanism. The object of a miner is to score higher than their peers and not fall into the bottom percentile and risk reregistration.  The longer a miner remains active, the more profitable they become. Miners may operate multiple nodes on multiple subnets.

When mining, miners ensure that their servers are operating - accepting requests from validators and returning responses. Miners can modify their mining server and code to best meet the incentive mechanism for the subnet.

Mining is highly competitive - the "best" miners in each subnet accumulate more emissions, and the miners with the lowest scores are de-registered from the network.

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2F3pfPUFxhprY%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3D3pfPUFxhprY&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2F3pfPUFxhprY%2Fhqdefault.jpg&key=7788cb384c9f4d5dbbdbeffd9fe4b92f&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen; encrypted-media; picture-in-picture;\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=3pfPUFxhprY",
  "title": "Introduction to Mining on Bittensor",
  "favicon": "https://www.google.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/3pfPUFxhprY/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=3pfPUFxhprY",
  "typeOfEmbed": "youtube"
}
[/block]


<br />

# Creating a miner

The miner persona runs [MIner servers](doc:mining) in a subnet. To mine, research all of the subnets (see the [Bittensor Subnets](doc:list-of-subnets-1) list), and decide which subnet you wish to mine.  Each subnet has different hardware and software requirements.  Some subnets have a testnet to test your miner before registering and mining in the subnet.

You'll need to [register a node](doc:node-registration) with a Bittensor hotkey.  The you'll start your miner code on your server with the same hotkey to verify your server on the network.

# Ranking

Each miner participates in a subnet.  It solves the challenge specific to that subnet, and the miner's responses are evaluated by validators based on the subnet's criteria. The validators then weigh (or rank) the responses of all miners and rank them via weights. The weights are posted to [Yuma Consensus](doc:consensus) to create an incentive score - and the higher the incentive, the higher the reward. 

If a miner's server falls into the bottom of the miner trust rankings for a subnet, it risks being de-registered.

Reward for miners is scored as emission.

# Rewards

 Miners receive [tao](doc:tao-allocation) as an award for the work produced.  The reward is based on their ranking as scored by the specific subnet's incentive mechanism.

The emission scores for all miners sum to 1.  This is then used to allocate the emissions awarded to the miners.

The [Tao Allocation](doc:tao-allocation) page describes how tao is distributed in the Bittensor ecosystem.  

# Helpful links

- [Taostats: For Miners](doc:taostats-for-miners)