---
title: 'Staking: Taostats Subnet page'
excerpt: You can now stake right on the Subnet page
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
<Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=zbxMMvlrZ24" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252FzbxMMvlrZ24%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253DzbxMMvlrZ24%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252FzbxMMvlrZ24%252Fhqdefault.jpg%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" href="https://www.youtube.com/watch?v=zbxMMvlrZ24" providerUrl="https://www.youtube.com/" providerName="YouTube" />

<br />

On each subnet page, there is the ability [to connect your wallet](doc:connecting-your-wallet) and stake to the subnet.

![](https://files.readme.io/cc4aa9a73daa1baf9bea31469d565e6e3698615fe41650c5853b6db0f986789a-image.png)

<br />

In the screenshot above:

* there is 3.66 tao that can be used to buy alpha.
* There is 0.149 alpha that cann be sold for tao

## Max

clicking the Max button will use all of your available tao/alpha to buy/sell. The slippage number will update with the estimated slippage for the transaction.

![](https://files.readme.io/b23fa4116b9ba5cff2cf2720d7dd818273246cdaa8c8f243a866dd0d6e66dee6-image.png)

## Buy/Sell

On clicking the buy or sell button, a popup will appear:

![](https://files.readme.io/4644c66a923093dad73083edabf7e698c387326c58431e2c113de077068432bc-image.png)

Clicking confirm will open a dialoge from your wallet application confirming the sale:

## Settings

Adjust your validator of choice, and the amount of slippage that is acceptable

![](https://files.readme.io/6ec4cce53cbff9778692d7ef2bd16c816a02b5ab2ba2cf982a6adf58ff7ad131-image.png)

<br />

## Fees

There are staking and unstaking fees on Bittensor.  

* Root subnet: no staking or unstaking fees
* Fee is a percentage (that can be adjusted by the subnet owner.  
  * Fee is taken as tao when staking
  * Fee is taken as alpha when unstaking

<StakingFee2 />

If you utilize multiple staking actions using taostats, they will be sent to the chain in a `batch`.  Batch calls on chain have a small fee.  Taostats does not collect this fee, it is paid to the chain.

<br />

# [Stake troubleshooting](doc:stake-troubleshooting)
