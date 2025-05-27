---
title: dTao Introduction
excerpt: >-
  An introduction to the dTao launch, and new features in the dTao version of
  Bittensor
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  image: >-
    https://files.readme.io/f86296ae834d0d7f972da557695813f19c7356ab980e413df2d05f8646c09373-5c7ec0ef615eab848d8b67f51dc7420704504a7c21a179b3ce401ee84528e5bc-taostats-docs.jpg
  robots: index
next:
  description: ''
---
dTao is a fundamental change to emission on Bittensor, launched on February 13, 2025.

<Embed url="https://www.youtube.com/watch?v=W-2usD9UCjI" href="https://www.youtube.com/watch?v=W-2usD9UCjI" typeOfEmbed="youtube" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252FW-2usD9UCjI%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253DW-2usD9UCjI%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252FW-2usD9UCjI%252Fhqdefault.jpg%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" />

<br />

# What is dTao?

dTao is a proposal to further decentralize the Bittensor ecosystem.  At its most basic, dTao introduces tokens for each subnet.  The subnet tokens are named after letters in the alphabet (subnet1 = alpha, Subnet2 = beta, etc. - with other alphabets following Greek), but are referred to in the generic sense as *alpha*. These tokens are traded with tao from the Bittensor chain.

> 📘 While each subnet has a token with a unique name, the term `alpha` is used to generally describe any subnet token.

## Why alpha tokens?

With alpha tokens, active participants in the Bittensor network can show their support of a subnet by buying that alpha and staking their alpha on the subnet.  The amount of alpha staked, and the exchange rate for the subnet will now play a role in determining the emission earned by the subnet.

See [Alpha Tokens](doc:alpha-tokens) for more detail.

## How does emission change with dTao?

The [Subnet Emission](doc:subnets-emission) section walks through how alpha is distributed inside a subnet.

## Does my staking change in dTao?

Any tao staked prior to dTao is now staked to root. This was done automatically.  Basic staking is now called "Root Stake" or "staking to root."

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