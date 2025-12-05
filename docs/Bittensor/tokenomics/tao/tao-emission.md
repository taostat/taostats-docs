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

Starting in November 2025, tao flow will begin to be a part of the tao emission equation. By December 2025, 100% of tao emitted will be based on tao flow.

<br />

## What is flow

In every subnet, tao flows in and out of the liquidity pool through staking actions:

<Image border={false} src="https://files.readme.io/a4a27b0628a0677e0098b226e7194c74cca4743af7c60b5d6d5f008c7b445cbc-image.png" />

Flow is _only staking_ it is **NOT** based on emission, root proportion or neuron registration.

To smooth this equation, each subnet's flow is placed in an exponential moving average with a half life of 30 days:

<Image border={false} src="https://files.readme.io/8117fca83f79395f015b74a589d28e86255e55bd14509aae1ba8ab3d38554c1b-image.png" />

<br />

Now this flow can still be negative- and we cannot have a negative flow (removing tao from the subnet), so we only use flow EMAs that are. above zero.. and those below zero are set to zero.

<Image border={false} src="https://files.readme.io/e49a805e14d5a891c90e671aa3a79efc672ee989a31ad33dc35030790f0d8f85-image.png" />

We can then normalize the flows across all subnets:

<Image border={false} src="https://files.readme.io/79529d16e10dd4bed95c7ed1badfc850bd06830ca75c59f1bcb083a88c6dbdc4-image.png" />

<br />

<br />
