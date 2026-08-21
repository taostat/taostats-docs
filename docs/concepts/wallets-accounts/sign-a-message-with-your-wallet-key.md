---
title: Sign a message with your wallet key
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

One way to prove ownership of a wallet is to sign a message.  This can be done with the [polkadot website](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Farchive.chain.opentensor.ai%3A443#/signing)

Import your wallets, and choose the wallet you would like to sign the message with.

<Image border={false} alt="Wallet message-signing panel with an account selector, message field, hex-input toggle, resulting signature field with copy button, and a Sign message button" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/94961ff9dab27e65.png" />

Here, the wallet rao has signed the message "I like taostats."  To sign this message, the owner has to enter their wallet's password. So only the owner of the wallet can create the signature.

## Decrypting the signature

The other party has your wallet address, and the signature.

Click the verify tab from the link above.

<Image border={false} alt="Signature verify form with address selector, signed-data field, a signature field showing a green valid checkmark, crypto-type, and hex-input fields" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/53619626e9a69034.png" />

The green checkmark indicates success!

Whoever created that signature has possession of the wallet.
