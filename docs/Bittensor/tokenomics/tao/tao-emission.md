---
title: Tao Emission
excerpt: Basics on how tao is emitted and distributed in Bittensor.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Every block, 1 tao is emitted by the chain (until 10.5M blocks are emitted and the first [Halving](doc:halving) occurs).  Where do these blocks go?

The tao is divided amongst the subnets and the fraction of tao awarded to each subnet is placed into the `tao_in` of the [Subnet Pools](doc:subnet-pools).

<Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=9WYteMtyeLA" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252F9WYteMtyeLA%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253D9WYteMtyeLA%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252F9WYteMtyeLA%252Fhqdefault.jpg%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" href="https://www.youtube.com/watch?v=9WYteMtyeLA" providerUrl="https://www.youtube.com/" providerName="YouTube" />

<br />

# Flow based emission

<br />

<br />

# Price based emission

<br />

Tao emission (also known as `tao_in`) on a subnet is calculated by finding the subnet price, and dividing by the total of all subnet prices. This approach is being phased out, and will be no longer used in the network by December 2025.

This ensures that 1 tao is emitted every block, and distributed amongst the subnets.

<Image border={false} src="https://files.readme.io/2a743d39d2afaacc67b13c59c53b76b57ba794a23d89d4fea557fc1da1d76cb4-image.png" />

> 📘 Tao_in example:
>
> If the Sum of all prices is 1.8, and the price for a Subnet is 0.2.
>
> tao_in will be 0.2/1.8 = .111 per block.

<br />

### Caveat:

In reality, the tao_in is determined by an Exponential Moving Average (EMA) of price, but in most cases, the simple illustration above is good enough.
