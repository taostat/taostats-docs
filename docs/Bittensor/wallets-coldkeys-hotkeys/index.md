---
title: Wallets
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Wallets are used to store and house your tokens.  But the term wallet can be used for a few different things in the Bittensor ecosystem.

<Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=ZC2z4asAMl0" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252FZC2z4asAMl0%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253DZC2z4asAMl0%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252FZC2z4asAMl0%252Fhqdefault.jpg%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" href="https://www.youtube.com/watch?v=ZC2z4asAMl0" providerUrl="https://www.youtube.com/" providerName="YouTube" />

<br />

# Wallet application

Wallet applications are the way you interact with your tao on chain.  There are many wallets (The Bittensor Discord has a [FAQ](https://discord.com/channels/799672011265015819/1215386737661055056/1220037507656450068)  listing the wallets that support Bittensor.)  No matter what wallet application you use, the wallet is just looking at your tao on the chain.

## Taostats wallets

We think the taostats wallet applications are pretty good!

### [Chrome extension](https://chromewebstore.google.com/detail/taostats-the-bittensor-wa/khdnjjgidjjbjpececegbfglalchffpo)

### [Mobile apps](https://taostats.io/app)

<br />

> 📘 Banking
>
> When you access your bank account, you use the mobile app, the website, an ATM, or even a bank teller in the bank.  These are all interfaces into your bank account.
>
> None of these interfaces hold the money in your account, but are access points to the bank to manipulate your money.  You can take money in and out, pay bills, etc.from the interfaces in your account.

You can connect many wallets to the [taostats delegation app](https://delegate.taostats.io) .  Once connected you can add/remove stake to validators using taostats.  (Taostats has no access to your wallet - the actions are all performed by the wallet app on chain).

You can also use the [Command Line Interface (CLI)](doc:command-line-tool) to interact with your wallet without using a wallet application.

Your tao is always stored on chain, and the application wallet is a way to gain access to that tao.

## Switching wallet applications

When changing your wallet applications - you do not need to do anything with your tao.  You can just connect your coldkey wallet to the new interface. This is done by using your 12 word mnemonic to regenerate the wallet in the new interface.  You can then remove the your wallet from the old application.  We do not recommend removing a wallet application interface before addeing the new interface - just in case there is an error.

### Things you do not have to do when switching wallet applications

![](https://files.readme.io/b7b0cfcc2e32385c66da8f90b414b3d78c6fc956bf328d70fcf3d00761f1c380-image.png)

<br />

> 📘 Banking
>
> "I no longer want to use my bank's mobile app, I want to use the website.  In order to switch, I closed my savings account in the mobile app. I then logged in on my bank's website, and opened a savings account there."

By unstaking your tao, you lose rewards for a period backwards in time (this can be up to 24 hours!)  When restaking - you lose rewards for a period of time in the future (this can be up to 24 hours!).  While it is unlikely that you will lose rewards for 48 hours, it is possible.

<br />

# Coldkey Wallet

Your coldkey wallet is stored on the Bittensor chain and holds your tao.  The chain acts as the "bank" for your wallet address and stores your funds and transaction history.  For this reason, it is essential that your coldkey be kept secure.

See [Coldkeys](doc:coldkeys) for more detail.

> 📘 Banking
>
> The coldkey wallet on the chain is equivalent to your bank account in the vault. Anyone with access to the money in your account can add or extract from the vault.

# Hotkey

Hotkeys are used on chain. If you run a validator or miner, you use a hotkey (associated to a coldkey).  If you stake tao, you are also using a hotkey.  All tao/alpha on a hotkey is controlled by the owner of the coldkey.  This means that staked tao/alpha is fully under your control, as are the emissions earned by miners/validators.

See [Hotkeys](doc:hotkeys) for more detail.
