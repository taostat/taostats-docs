---
title: Coldkey uses
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

The coldkey is your wallet on the chain. It is used for tao storage and transferring tao to and from others. Coldkeys can have hotkeys for performing tasks on chain.

* Funds in your coldkey can be transferred in and out of your coldkey.
* Subnets are registered on a coldkey, using the funds on that coldkey.
* Delegation to validators.  The tao on your coldkey can be delegated to the hotkey of a validator.

# Create a coldkey wallet

In the btcli:`btcli wallet create`

Using Polkadot JS extension:

1. Create new account

   <Image border={false} alt="Dark-themed wallet toolbar with search, an orange add button, and settings, plus a dropdown offering a Create new account option" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/e987b7d8444185f2.png" />

In all cases, you will be provided with a 12 word mnemonic/seed phrase.  it is **very important** to keep this phrase in a safe place.

<Image border={false} alt="Wallet screen displaying a generated 12-word mnemonic seed phrase in a bordered box under an uppercase label" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/364811ed36af2341.png" />

> 📘 **Key type and address format**
>
> Coldkeys and hotkeys are **sr25519** keypairs. Addresses use the SS58 format with Bittensor's network prefix **42** (an address such as `5F...`). The 12-word mnemonic is the only recovery path — the wallet password only decrypts the keyfile on one machine; anyone holding the mnemonic can regenerate the key and controls the funds.

> 🚧 **NEVER, EVER provide your mnemonic/seed phrase to "support."**
>
> Anyone with your seed phrase has full access to your wallet.

3. This will generate a coldkey public hash/public key that looks like `5E6yV6xPjFrYv167nXaMhdmZUwMR5QM1M9jJhL85QPhi2DYc`. For Bittensor, all keys will begin with a 5.

# Coldkey security

Your coldkey public key (`5E6yV6xPjFrYv167nXaMhdmZUwMR5QM1M9jJhL85QPhi2DYc`) is public and can be searched on taostats to display you your balance, transactions, etc.  Who owns the coldkey is anonymous.

Others can *send* tao to your cold key, but only you can withdraw from your coldkey.

Your mnemonic phrase allows you to add your coldkey into wallet applications.  You can import existing coldkeys into wallet apps, etc.  However, *anyone* can add a wallet with the 12 word phrase, including scammers.  If you believe your coldkey has been compromised, you can perform a coldkey swap.

## Coldkey swap

A coldkey swap will lock the funds on your coldkey for 5 days, and after 5 days, the funds will be available on a new coldkey. The delay prevents bad actors from swapping coldkey access away from existing users. This is available today via `btcli wallet swap_coldkey`.

# Hotkeys

Hotkeys are connected to the cold key, and used for performaing transactions on chain.  See [Hotkeys](/docs/hotkeys) for details.
