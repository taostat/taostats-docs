---
title: Wallet application
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

Wallet applications are the way you interact with your tao on chain.  There are many wallets (The Bittensor Discord has a [FAQ](https://discord.com/channels/799672011265015819/1215386737661055056/1220037507656450068)  listing the wallets that support Bittensor.)  No matter what wallet application you use, the wallet is just looking at your tao on the chain.

## Taostats wallets

We think the taostats wallet applications are pretty good!

### [Chrome extension](https://chromewebstore.google.com/detail/taostats-the-bittensor-wa/khdnjjgidjjbjpececegbfglalchffpo)

### [Mobile apps](https://taostats.io/app)

> 📘 **Banking**
>
> When you access your bank account, you use the mobile app, the website, an ATM, or even a bank teller in the bank.  These are all interfaces into your bank account.
>
> None of these interfaces hold the money in your account, but are access points to the bank to manipulate your money.  You can take money in and out, pay bills, etc.from the interfaces in your account.

You can connect many wallets to the [taostats delegation app](https://delegate.taostats.io) .  Once connected you can add/remove stake to validators using taostats.  (Taostats has no access to your wallet - the actions are all performed by the wallet app on chain).

You can also use the [Command Line Interface (CLI)](/docs/command-line-tool) to interact with your wallet without using a wallet application.

Your tao is always stored on chain, and the application wallet is a way to gain access to that tao.

## Switching wallet applications

When changing your wallet applications - you do not need to do anything with your tao.  You can just connect your coldkey wallet to the new interface. This is done by using your 12 word mnemonic to regenerate the wallet in the new interface.  You can then remove the your wallet from the old application.  We do not recommend removing a wallet application interface before addeing the new interface - just in case there is an error.

### Things you do not have to do when switching wallet applications

<Image border={false} alt="Dark-themed Discord chat message describing unstaking from one wallet app and re-staking in another via a hardware device" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/83d19b962fcb497f.png" />

> 📘 **Banking**
>
> "I no longer want to use my bank's mobile app, I want to use the website.  In order to switch, I closed my savings account in the mobile app. I then logged in on my bank's website, and opened a savings account there."

By unstaking your tao, you lose rewards for a period backwards in time (this can be up to 24 hours!)  When restaking - you lose rewards for a period of time in the future (this can be up to 24 hours!).  While it is unlikely that you will lose rewards for 48 hours, it is possible.

# Coldkey Wallet

Your coldkey wallet is stored on the Bittensor chain and holds your tao.  The chain acts as the "bank" for your wallet address and stores your funds and transaction history.  For this reason, it is essential that your coldkey be kept secure.

See [Coldkeys](/docs/coldkeys) for more detail.

> 📘 **Banking**
>
> The coldkey wallet on the chain is equivalent to your bank account in the vault. Anyone with access to the money in your account can add or extract from the vault.

# Hotkey

Hotkeys are used on chain. If you run a validator or miner, you use a hotkey (associated to a coldkey).  If you stake tao, you are also using a hotkey.  All tao/alpha on a hotkey is controlled by the owner of the coldkey.  This means that staked tao/alpha is fully under your control, as are the emissions earned by miners/validators.

See [Hotkeys](/docs/hotkeys) for more detail.

# Securing your wallet

Because your coldkey controls your funds on chain, securing it is essential. Bittensor supports several complementary approaches — hardware ledgers, multisignature accounts, and proxy accounts — that can be combined for defence in depth.

- [Securing a wallet: ledgers, multisig & proxies](/docs/securing-a-wallet) — the threat model and when to use each approach.
- [Multisig, explained: tutorial](/docs/multisig-tutorial) — how multisignature wallets work, step by step.
- [Multisig: worked examples](/docs/multisig-examples) — real multisig flows decoded from the chain.

For the chain-level detail, see [Multisig extrinsics](/docs/multisig-extrinsics) and [Proxy extrinsics](/docs/proxy-extrinsics).
