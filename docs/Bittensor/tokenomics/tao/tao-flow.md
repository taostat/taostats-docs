---
title: Tao Flow & Net Tao Flow
deprecated: false
hidden: false
metadata:
  robots: index
---
As of May 2026, there are two types of tao flow.  The article attempts to first disambiguate them and then define them, and their uses.

Net Tao Flow: is currently in the dev branch, and is scheduled to be released end of May.  There is a toggle on chain that allows a SUDO call to switch between NetTaoFlow and TaoFlow.

# Tao Flow

Introduced in November 2025, tao flow is the measurement of staking and unstaking through the subnet liquidity pool.  Its original use was to determine the emissions of a subnet.  This changed in May 2026, with the introduction of Net Tao Flow.

In the May 2026 release, all neuron purchases (tao added to the pool, alpha is recycled) are inclided as a tao_staked, an inflow.

Tao flow is still an interesting figure - it is a measure of how stakeholders are entering and exiting the subnet.

![](https://files.readme.io/a4a27b0628a0677e0098b226e7194c74cca4743af7c60b5d6d5f008c7b445cbc-image.png)

# Net Tao Flow

Introduced in May 2026 to counteract issues with tao flow.  The principal issue is that while tao flow is a good metric, it does not account for subsidies from the chain.  A new term, Protocol cost is added.

![](https://files.readme.io/278af04c53eed397a917aa838a7e2307715199115112a71e94d3b51c91651fbe-image.png)

If netTaoFlow {'<0'}, it is set at 0 - there is no concept of negative emission.

But to smooth these values, a 30 day [exponential moving average](#https://docs.taostats.io/docs/tao-flow#exponential--moving-average-example) is used for both.

![](https://files.readme.io/2cd1b1a7f150cffecc78c4c0372b64d4adb196f77c0c77dcf8e27b3727531624-image.png)

This new term is used to define the emissions delivered to a subnet.

## Protocol cost

Each block, the subnet is subsidized by [Tao Emission ](doc:tao-emission) - broken into Tao injected into the pool and chain buys.  Root sells of alpha work in the opposite direction: when validators claim and swap their root‑alpha dividends, TAO leaves the pool, offsetting part of the subsidy.

![](https://files.readme.io/6fc9cef6dfc9c3710710b9d34cdc5c472560aabc390bb69dfb1febe15aa27c5a-image.png)

<br />

### Exponential  Moving Average example

To smooth this equation, each subnet's flow is placed in an exponential moving average with a half life of 30 days:

![](https://files.readme.io/8117fca83f79395f015b74a589d28e86255e55bd14509aae1ba8ab3d38554c1b-image.png)

Both TaoFlow and NetTaoFlow have the same EMA.

# Emission calculation from tao flow.

In every subnet, tao flows in and out of the liquidity pool through staking actions:

Flow is _only staking_ it is **NOT** based on emission, root proportion or neuron registration.We can then normalize the flows across all subnets:

![](https://files.readme.io/79529d16e10dd4bed95c7ed1badfc850bd06830ca75c59f1bcb083a88c6dbdc4-image.png)

<Callout icon="📘" theme="info">
  Note: this is the total tao_in.  The this is then split into [Tao Emission ](doc:tao-emission) and  [Tao Excess](doc:tao-emission-does-not-add-to-100).  This occurs when price and default tao emission result in "too much" alpha_in injected into the pool.

  The alpha_in is scaled to it's maximum emission, which results in scaling down the tao_in.  The difference is called excess tao.
</Callout>

<br />

This video explains the launch of tao flow (the original in November 2025). It is somewhat dated, but many of the major points still hold.

<Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=9WYteMtyeLA" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252F9WYteMtyeLA%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253D9WYteMtyeLA%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252F9WYteMtyeLA%252Fhqdefault.jpg%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" href="https://www.youtube.com/watch?v=9WYteMtyeLA" providerUrl="https://www.youtube.com/" providerName="YouTube" />

<br />
