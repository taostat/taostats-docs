---
title: dTao Introduction
excerpt: This page is accurate as of January 27, 2025.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  image: >-
    https://files.readme.io/f86296ae834d0d7f972da557695813f19c7356ab980e413df2d05f8646c09373-5c7ec0ef615eab848d8b67f51dc7420704504a7c21a179b3ce401ee84528e5bc-taostats-docs.jpg
  robots: index
next:
  description: ''
---
dTao is a proposal to change the way emission is distributed in Bittensor, poised to launch in February 2025.

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FW-2usD9UCjI%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DW-2usD9UCjI&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FW-2usD9UCjI%2Fhqdefault.jpg&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen; encrypted-media; picture-in-picture;\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=W-2usD9UCjI",
  "title": "Bittensor - Introduction to Dynamic TAO",
  "favicon": "https://www.youtube.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/W-2usD9UCjI/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=W-2usD9UCjI",
  "typeOfEmbed": "youtube"
}
[/block]


<br />

# What is dTao?

dTao is a proposal to further decentralize the Bittensor ecosystem.  At its most basic, dTao introduces tokens for each subnet.  The subnet tokens are named after letters in the alphabet (subnet1 = alpha, Subnet2 = beta, etc. - with other alphabets following Greek), but are referred to in the generic sense as _alpha_. These tokens are traded with tao from the Bittensor chain. 

> 📘 While each subnet has a token with a unique name, the term `alpha` is used to generally describe any subnet token.

## Why alpha tokens?

With alpha tokens, active participants in the Bittensor network can show their support of a subnet by buying that alpha and staking their alpha on the subnet.  The amount of alpha staked, and the exchange rate for the subnet will now play a role in determining the emission earned by the subnet.  

See [Alpha Tokens](doc:alpha-tokens) for more detail.

## How does emission change with dTao?

The [Subnet Emission](doc:subnets-emission) section walks through how alpha is distributed inside a subnet.  

## Does my staking change in dTao?

Any tao staked prior to dTao is now staked to root. This will be done automatically for you.

[Stakeholder Emissions: Root](doc:stakeholder-emissions-root)

> 📘 Staking actions now have a cost.
> 
> All staking actions now incur a staking fee set at  .0005 tao (500,000 rao)

# Reading material

The [Dtao proposal](https://github.com/Datura-ai/bit001/blob/main/bit001_1.pdf) (PDF format) - This is the original article describing the dtao proposal.  The current dtao  draws implementation from this article. A new version is in the works.

The [Bittensor-Rao Discord channel](https://discord.com/channels/799672011265015819/1230665820859007039).  This is the best place to keep up to date on the dtao proposal.

[Dtao emissions for stakeholders](https://mentat-minds.notion.site/How-does-the-Dynamic-TAO-staking-mechanism-work-13511a348a4e8073b51ef77edf5e3dd9).  A mathematical summary of how emission is distributed to validators.

[dtao simulation](https://github.com/learnbittensor/rao-simulation) Python simulation of stakeholder emissions

# Understanding the CLI

[Create Wallets & Register Subnets](doc:create-wallets-register-a-validator)

[btcli tables in Bittensor-Rao](doc:btcli-tables-in-bittensor-rao)

<br />

# New Terms

[Dtao Glossary](doc:dtao-glossary)