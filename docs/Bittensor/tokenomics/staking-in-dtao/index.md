---
title: Staking
excerpt: Learn about staking to root and alpha, and how these emissions are divided up.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
> 📘 Staking with taostats
>
> See [Staking Instructions](doc:staking-instructions) for a number of pages describing how to stake using Taostats.

<br />

Staking plays a principal role in the functioning of the Bittensor network. The principal goal of dTao is to divide chain emissions amongst subnets in a democratic way.  Staking into a subnet  increases the emissoins of the subnet.

# Subnet emission

Emission into a subnet is determined by the subnet price. (which is based on the amount of tao and alpha in the [Subnet Pool](doc:subnet-pools). The act of staking adds tao and removes alpha from the pool, increasing the price, and increasing emission to the subnet. Therefore subnet emission is guided by how much stake has been placed on the subnet.

# Staking Options

in dTao, there are two options for staking:

* [Staking to root](#staking-to-root)
* [Staking to a Subnet](#staking-to-alpha)

## Emission division: root to subnet

Stakeholder emission is split between these two options.  For new subnets, the emission is primarily to root, with subnet increasing over time

<Image align="center" alt="An example breakdown of root:subnet proportions." border={false} caption="An example breakdown of root:subnet proportions." src="https://files.readme.io/3e9d7b5c3747867d7b1d97a068bfceb15d003e0f4ba498f2f5b48bcca74f11ac-image.png" />

<br />

This change over time is described in [Emissions: Root vs. Alpha Stake](doc:stakeholder-emissions-root-vs-alpha).

## Staking to root

Staking to root does not affect subnet emissions, and is a `safe`  staking option - there is no way to lose tao value.   Root stakers earn a (ever decreasing) portion of returns from every subnet the validator is active in.

If you have staked to root, your returns will be auto-compounded to your hotkey on root.

## Staking to alpha

This is the new feature and primary goal of dTao - to enable stakeholders to vote and determine the emissions for every subnet.

To stake in alpha, tao is exchanged via the [Subnet Pools](doc:subnet-pools) into alpha.  This will incur [Slippage](doc:slippage). The received alpha is then staked to the validator selected.  Your returns will be in alpha, and autocompounded to the validator hotkey.

Staking to alpha *does* incur risk: a drop in alpha token price will result in a lower amout of tao when unstaking.

<br />

> 📘 Staking fees
>
> ## Root
>
> All staking and unstaking actions incur a fee of 50,000 rao (0.00005 tao).
>
> ## Subnets not on UniswapV3
>
> * Staking: All staking actions will incur a 50,000 rao (0.00005 tao) fee.
> * Unstaking:
>   * Unstaking from root is set at 50,000 rao
>   * Alpha unstaking: The minimum fee is 50,000 rao (0.00005 tao).
>     * The max is a percentage of your alpha emission:
>     * AlphaEmission\_epoch: the amount your coldkey earns in 360 blocks
>     * alpha\_unstaked/alpha\_staked = this is the % of alpha that you unstake.,
>     * alpha\_price - the fee is paid in tao, so it is converted via the price.
>     * ![](https://files.readme.io/28fa9a6eacaebe6e2ddafd2c10a776896dcbb0bc2a8f92017cdb45083c480d4a-image.png)
>
> Example unstaking:
>
> You earn 10 alpha per epoch, and you unstake 50% of your alpha.  The fee will be 10\_50% = 5 alpha\_alpha\_price
>
> ## Subnets on UniswapV3:
>
> * All staking and unstaking fees are 0.3% of the stake/unstake value.
>
> <Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=5VhvUHxqQNE" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252F5VhvUHxqQNE%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253D5VhvUHxqQNE%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252F5VhvUHxqQNE%252Fhqdefault.jpg%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" href="https://www.youtube.com/watch?v=5VhvUHxqQNE" providerUrl="https://www.youtube.com/" providerName="YouTube" />

## [dTao FAQ](doc:dtao-faq): Your top  staking questions