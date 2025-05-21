---
title: Coldkeys
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

# Coldkey uses

- Funds in your coldkey can be transferred in and out of your coldkey.
- Subnets are registered on a coldkey, using the funds on that coldkey.
- Delegation to validators.  The tao on your coldkey can be delegated to the hotkey of a validator.

# Create a coldkey wallet

In the btcli:`btcli wallet create`

Using Polkadot JS extension:

1. Create new account

   [block:image]{"images":[{"image":["https://files.readme.io/dd1481ec61b22a5da318f44dd45789d1e915e99fc7227aab161fe5cccead4535-image.png",null,""],"align":"center","sizing":"25% "}]}[/block]

In all cases, you will be provided with a 12 word mnemonic/seed phrase.  it is **very important** to keep this phrase in a safe place.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d5baffb5435600e1bcaca17e9ce07588c2db87c0bd64d978bc4c16b6f933cfd3-image.png",
        null,
        ""
      ],
      "align": "center",
      "sizing": "25% "
    }
  ]
}
[/block]


> 🚧 NEVER, EVER provide your mnemonic/seed phrase to "support."
> 
> Anyone with your seed phrase has full access to your wallet.

3. This will generate a coldkey public hash/public key that looks like `5E6yV6xPjFrYv167nXaMhdmZUwMR5QM1M9jJhL85QPhi2DYc`. For Bittensor, all keys will begin with a 5.

# Coldkey security

Your coldkey public key (`5E6yV6xPjFrYv167nXaMhdmZUwMR5QM1M9jJhL85QPhi2DYc`) is public and can be searched on taostats to display you your balance, transactions, etc.  Who owns the coldkey is anonymous.

Others can _send_ tao to your cold key, but only you can withdraw from your coldkey.

Your mnemonic phrase allows you to add your coldkey into wallet applications.  You can import existing coldkeys into wallet apps, etc.  However, _anyone_ can add a wallet with the 12 word phrase, including scammers.  If you believe your coldkey has been compromised, you can perform a coldkey swap.

## Coldkey swap

A coldkey swap will lock the funds on your coldkey for 5 days, and after 5 days, the funds will be available on a new coldkey.  The delay prevents bad actors from swapping coldkey access away from existing users.  This will be available in the btcli soon.

# Hotkeys

Hotkeys are connected to the cold key, and used for performaing transactions on chain.  See [Hotkeys](doc:hotkeys) for details.