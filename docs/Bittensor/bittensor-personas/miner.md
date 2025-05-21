---
title: Miner
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

<Embed url="https://www.youtube.com/watch?v=3pfPUFxhprY" title="Introduction to Mining on Bittensor" favicon="https://www.google.com/favicon.ico" image="https://i.ytimg.com/vi/3pfPUFxhprY/hqdefault.jpg" provider="youtube.com" href="https://www.youtube.com/watch?v=3pfPUFxhprY" typeOfEmbed="youtube" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252F3pfPUFxhprY%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253D3pfPUFxhprY%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252F3pfPUFxhprY%252Fhqdefault.jpg%26key%3D7788cb384c9f4d5dbbdbeffd9fe4b92f%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" />

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

* [Taostats: For Miners](doc:taostats-for-miners)
