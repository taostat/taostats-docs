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

> The [Miner persona](doc:miner) has details on how a miner can be run.

Miners produce output as defined by the subnet code. As miners are only scored by validators and there is no incentive for them to receive or trust requests from anyone else, all requests to the miners pass through a validator.

![](https://files.readme.io/7f1f48b-image.png)

# Hardware requirements

Mining hardware requirements vary by subnet although most require some for of GPU to perform the require compute functions. Each subnet's github repository should have a `min_compute.yml` or information in the readme, describing the hardware requirements for mining the subnet. See: [Bittensor Subnets](doc:list-of-subnets-1) for links.

<Embed 
  url="https://www.youtube.com/watch?v=3pfPUFxhprY" 
  title="Introduction to Mining on Bittensor" 
  favicon="https://www.google.com/favicon.ico" 
  image="https://i.ytimg.com/vi/3pfPUFxhprY/hqdefault.jpg" 
  provider="youtube.com" 
  href="https://www.youtube.com/watch?v=3pfPUFxhprY" 
  typeOfEmbed="youtube" 
  html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252F3pfPUFxhprY%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253D3pfPUFxhprY%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252F3pfPUFxhprY%252Fhqdefault.jpg%26key%3D7788cb384c9f4d5dbbdbeffd9fe4b92f%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" 
/>

<br>

# Miner Trust/Incentive

Each miner works to maximise their trust and incentive metrics on the network. This is done by meeting the validation requirements for the subnet at a higher level than their peers. Each validator will grade the results of the miner, assigning a score. Each epoch, the incentive scores (weights) are aggregated by the consensus mechanism to determine the miner's emissions.

See [Incentive for Miners](doc:consensus-for-miners) for a detailed breakdown of how minder incentive is calculated.

<Embed 
  url="https://www.youtube.com/watch?v=Z2s7jEJK_m4" 
  favicon="https://www.google.com/favicon.ico" 
  image="http://i.ytimg.com/vi/Z2s7jEJK_m4/hqdefault.jpg" 
  provider="youtube.com" 
  href="https://www.youtube.com/watch?v=Z2s7jEJK_m4" 
  typeOfEmbed="youtube" 
  title="undefined" 
  html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252FZ2s7jEJK_m4%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253DZ2s7jEJK_m4%26image%3Dhttp%253A%252F%252Fi.ytimg.com%252Fvi%252FZ2s7jEJK_m4%252Fhqdefault.jpg%26key%3D7788cb384c9f4d5dbbdbeffd9fe4b92f%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" 
/>

<br>

# Miner Registration

Learn how to [register a node](doc:node-registration) on a subnet.