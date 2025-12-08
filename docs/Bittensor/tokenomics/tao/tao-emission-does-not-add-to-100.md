---
title: Tao Emission does not add to 100%
excerpt: Why does the tao emission not always add up to 100%
deprecated: false
hidden: false
metadata:
  robots: index
---
Looking at the Taostats Subnet page, you may notice that the Emissions do not always add to 100%  

<Image border={false} caption="Here they add to 92.7%" src="https://files.readme.io/af2f0aba280752fe8f557ed71d3e5b17b7872c91166f6d304c84909bee0eed79-image.png" />

<br />

If 1 tao is emitted per block, this means that just 0.817 tao is being awarded to subnets. Where is the other .183 ao going?

# The chain is buying this tao and injecting it into subnet Liquidity pools.

<br />

## Why??

<br />

[Tao Emission](doc:tao-emission) is calculated from EMA flow.

[Alpha Emission](doc:alpha-emission) is calculated from tao emission and price - but it has a max value of 1. 

<br />

At the time of writing, Subnet 8 has:

*  a normalized EMA flow of 0.05635527424782002. 
* Price is 0.035997

This would mean that alpha_in should be 1.55 

<Image border={false} src="https://files.readme.io/5c48f4a34eb88388319d1a25fd2948c7b2b6a71b2039018357d5f36914ba5c9e-image.png" />

But since the maximum alpha that can be emitted into the pool is one, this is not possible.

So we reset alpha_in to 1, and calculate the tao_in:

<Image border={false} src="https://files.readme.io/6b995ed89549662efff0fcb37e076da0a53f94b794458177d7518f957cc25327-image.png" />

The tao_in cannot exceed 0.036997.

We have what is called `excess tao`  = default_tao_in - tao_in

<Image border={false} src="https://files.readme.io/c1a3fb7b53e64d92a7ac2c445a6f0657e0e7483817ede43f596b89394cb8686e-image.png" />

On SN 8 there is 0.0204 excess tao per block.

This tao is added to the liquidity pool, and the received alpha is recycled.

This serves to increase the price to nearer the emission percentage.

<br />

<br />

<br />

<br />

<Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=p9ZqN8oVEHU" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252Fp9ZqN8oVEHU%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253Dp9ZqN8oVEHU%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252Fp9ZqN8oVEHU%252Fhqdefault.jpg%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" href="https://www.youtube.com/watch?v=p9ZqN8oVEHU" providerUrl="https://www.youtube.com/" providerName="YouTube" />

<br />
