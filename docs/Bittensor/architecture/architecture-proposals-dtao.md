---
title: Dtao Introduction
excerpt: This page is accurate as of January 10, 2025.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Bittensor-Rao is a proposal to change the way emission is distributed in Bittensor.  It is still in proposal stage, but there are many questions.  Here we will attempt to answer.  This page will evolve as new information is revealed about the dtao proposal.

<Embed url="https://www.youtube.com/watch?v=0oSDxX_nN9M" title="Bittensor dtao: Introduction (as of November 11)" favicon="https://www.youtube.com/favicon.ico" image="https://i.ytimg.com/vi/0oSDxX_nN9M/hqdefault.jpg" provider="youtube.com" href="https://www.youtube.com/watch?v=0oSDxX_nN9M" typeOfEmbed="youtube" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252F0oSDxX_nN9M%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253D0oSDxX_nN9M%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252F0oSDxX_nN9M%252Fhqdefault.jpg%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" />

<br />

# What is dtao?

Dtao is a propsal to further decentralize the Bittensor ecosystem.  At it's most basic, dtao introduces tokens for each subnet.  The tokens are named alphabetically in Greek (subnet1 = alpha, Subnet2 = beta, etc.), but are referred to in the generic sense as *alpha*. These tokens are traded with tao from the Bittensor chain. 

## Why alpha tokens?

Currently, subnet emission is determined by a small group of validators placing weight on the [root subnet](https://docs.taostats.io/docs/root-subnet) .

Active participants in the Bittensor network can show their support of a subnet by buying that alpha and staking their alpha on the subnet.  The amount of alpha staked, and the exchange rate for the subnet will now play a role in determining the emission earned by the subnet.  

See [Alpha Tokens](doc:alpha-tokens) for more detail.

## How does emission change?

This is still a work in progress and is not finalized. The biggest change will be in how staking works.

[Staking in dtao](doc:staking-in-dtao)

# Reading material

The [Dtao proposal](https://github.com/Datura-ai/bit001/blob/main/bit001_1.pdf) (PDF format) - This is the original article describing the dtao proposal.  The current dtao  draws implementation from this article. A new version is in the works.

The [Bittensor-Rao Discord channel](https://discord.com/channels/799672011265015819/1230665820859007039).  This is the best place to keep up to date on the dtao proposal.

[Dtao emissions for stakeholders](https://mentat-minds.notion.site/How-does-the-Dynamic-TAO-staking-mechanism-work-13511a348a4e8073b51ef77edf5e3dd9).  A mathematical summary of how emission is distributed to validators.

[dtao simulation](https://github.com/learnbittensor/rao-simulation) Python simulation of stakeholder emissions

# Understanding the CLI

[Create Wallets & Register Subnets](doc:create-wallets-register-a-validator)

[btcli tables in Bittensor-Rao](doc:btcli-tables-in-bittensor-rao)

# Test it yourself

[Deploy Bittensor-Rao chain on Ubuntu](doc:deploy-dtao-chain-on-ubuntu)

[Deploy a Bittensor-Rao Chain on a Mac](doc:deploy-a-dtao-chain)

# New Terms

[Dtao Glossary](doc:dtao-glossary)
