---
title: Mev Shield
excerpt: why do we need mev shield, and how does it work?
deprecated: false
hidden: false
metadata:
  robots: index
---
<Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=WH9tJlXIuTE" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252FWH9tJlXIuTE%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253DWH9tJlXIuTE%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252FWH9tJlXIuTE%252Fhqdefault.jpg%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" href="https://www.youtube.com/watch?v=WH9tJlXIuTE" providerUrl="https://www.youtube.com/" providerName="YouTube" />

# MEVbots explained

Maximum Extractable Value (MEV) bots scan the chain and look for transactions to "steal" assets from.  There have been a number of approaches to hinder these Bots from operting on chain.

When a transaction moves through a liquidity pool, there is an oprotunity for slippage: where another transaction preceeds your transaction - changing the price, and effecting the amount of tao/alpha you receive.

<Callout icon="📘" theme="info">
  Example

  An isolated transaction will have a small price impact due to the liqudity pool

  <Image border={false} src="https://files.readme.io/01d19664e30b545aa236029a979017e5ab2aa2706e91c05508a3e75a2d82053a-image.png" />

  But a large transaction in front of this one adds slippage:  

  <Image border={false} src="https://files.readme.io/25389f78727e40ac3c144cc42e0f1b7ae86f5ff7cce16592d0b4d187d65e58cd-image.png" />

  In this example, 4% of the transaction is lost to slippage.  

  This is what the MEV bots do.
</Callout>

<br />

# First fix: Limits

All transactions should set a slippage limit.  This means - "hey, the price is x, and I am ok with a change of y% for the transaction."

The slippage limit should be small - a 4% slippage limit in the example above cost 20 alpha (~ 2 tao).  For high liquidity subnets, you can be well below 1%.

## The MEV bots calculate their MAX extraction on every transaction 

If your limit is very loose - the bot may decide to attack your transaction.

If you have no limit set:  The MEV bots can extract as much as they want.

<br />
