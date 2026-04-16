---
title: Bittensor Tax Reporting
excerpt: Taostats can help you prepare your income statements
deprecated: false
hidden: false
metadata:
  robots: index
---
No matter if you are a subnet owner, miner, validator, or you stake in Bittensor, eventually it will become time to report your actions on your taxes.

Bittensor is truly a global economy, and Taostats does not employ tax professionals, nor are we experts at global tax law.  But, we do have the data that can help you (or your tax professional) prepare your taxes.

At [https://taostats.io/pro/tax](https://taostats.io/pro/tax) , you can find tooling that provides you with annual returns for every token you have purchased in the Bittensor Network:

![](https://files.readme.io/a13c94fbeed25977fdcff237b6d6181f3b9ed47bfcd97153abe28f6594f9205d-image.png)

<br />

This reporting does require a paid Taostats plan.

<br />

For each subnet, you will receive a CSV.

<br />

Our reports are based on the following:

* the time zone is UTC - matching the blockchain time
* the daily income is attributed to the wallet on the last block of the day
* The subnet price is read from the chain on the last block of the day
* The USD/TAO uses the closing price from CMC (Coin market cap uses UTC)
* All transactions use the subnet price and CMC price at the time of the transaction (block)
* The subnet income reported is the sum from all sources (staking, owner, validating, mining)

<br />

# Using Taostats Tax Reporting

<Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=aUep2MgZhKE" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252FaUep2MgZhKE%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253DaUep2MgZhKE%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252FaUep2MgZhKE%252Fhqdefault.jpg%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" href="https://www.youtube.com/watch?v=aUep2MgZhKE" providerUrl="https://www.youtube.com/" providerName="YouTube" />

<br />

# Possible tax transactions:

**Here are the ones you will probably care about**
"transfer_out"
"token_swap"
"transfer_in"
"transaction_type"
"fee"

**But these also exist:**
"liquidity_fees_claimed"
"liquidity_added"
"coldkey_swap"
"dust_lost"
"tip"
"burned_register"
"liquidity_removed"
"subnet_registration_cost"

<br />
