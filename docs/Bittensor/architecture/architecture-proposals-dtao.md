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

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2F0oSDxX_nN9M%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3D0oSDxX_nN9M&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2F0oSDxX_nN9M%2Fhqdefault.jpg&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen; encrypted-media; picture-in-picture;\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=0oSDxX_nN9M",
  "title": "Bittensor dtao: Introduction (as of November 11)",
  "favicon": "https://www.youtube.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/0oSDxX_nN9M/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=0oSDxX_nN9M",
  "typeOfEmbed": "youtube"
}
[/block]


<br />

# What is dtao?

Dtao is a propsal to further decentralize the Bittensor ecosystem.  At it's most basic, dtao introduces tokens for each subnet.  The tokens are named alphabetically in Greek (subnet1 = alpha, Subnet2 = beta, etc.), but are referred to in the generic sense as _alpha_. These tokens are traded with tao from the Bittensor chain. 

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