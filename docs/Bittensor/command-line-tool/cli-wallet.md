---
title: 'CLI: Wallet'
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Actions around your Bittensor wallet.

```
btcli w  --help
                                                                                                                                                                       
 Usage: btcli w [OPTIONS] COMMAND [ARGS]...                                                                                                                            
                                                                                                                                                                       
╭─ Options ───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ --help          Show this message and exit.                                                                                                                         │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
╭─ Wallet Information ────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ balance            Check the balance of the wallet. This command shows a detailed view of the wallet's coldkey balances, including free and staked balances.        │
│ history            Show the history of the transfers carried out with the provided wallet on the Bittensor network.                                                 │
│ inspect            Displays the details of the user's wallet pairs (coldkey, hotkey) on the Bittensor network.                                                      │
│ overview           Displays a detailed overview of the user's registered accounts on the Bittensor network.                                                         │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
╭─ Wallet Management ─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ create             Create a complete wallet by setting up both coldkey and hotkeys.                                                                                 │
│ list               Displays all the wallets and their corresponding hotkeys that are located in the wallet path specified in the config.                            │
│ new-coldkey        Create a new coldkey. A coldkey is required for holding TAO balances and performing high-value transactions.                                     │
│ new-hotkey         Create a new hotkey for a wallet.                                                                                                                │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
╭─ Wallet Operations ─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ faucet             Obtain test TAO tokens by performing Proof of Work (PoW).                                                                                        │
│ sign               Allows users to sign a message with the provided wallet or wallet hotkey. Use this command to easily prove your ownership of a coldkey or a      │
│                    hotkey.                                                                                                                                          │
│ transfer           Send TAO tokens from one wallet to another wallet on the Bittensor network.                                                                      │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
╭─ Identity Management ───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ get-identity       Shows the identity details of a user's coldkey or hotkey.                                                                                        │
│ set-identity       Create or update the on-chain identity of a coldkey or a hotkey on the Bittensor network. Incurs a 1 TAO transaction fee.                        │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
╭─ Security & Recovery ───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ regen-coldkey      Regenerate a coldkey for a wallet on the Bittensor blockchain network.                                                                           │
│ regen-coldkeypub   Regenerates the public part of a coldkey (coldkeypub.txt) for a wallet.                                                                          │
│ regen-hotkey       Regenerates a hotkey for a wallet.                                                                                                               │
│ swap-hotkey        Swap hotkeys of a given wallet on the blockchain. For a registered key pair, for example, a (coldkeyA, hotkeyA) pair, this command swaps the     │
│                    hotkeyA with a new, unregistered, hotkeyB to move the original registration to the (coldkeyA, hotkeyB) pair.                                     │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
                                                                                                                                                                       
 Made with ❤ by The Openτensor Foundaτion                               
```

# Information

## list:

List all your wallets saved on your local computer.

```
btcli w list
Wallets
├── 
│   <walletname> (<coldkey>)
│   ├── <hotkey1 name> (<hotkey>)
│   ├── <hotkey2 name> (<hotkey>
<snip>
```

## overview

For a given wallet, displays all hotkeys currently registered on a network.

## balance

How much tao is available on each wallet: broken down by Free/staked and total.

## inspect

Lists all delegations and nodes registered for a specific coldkey.  Emission for both the delegation and nodes is also presented.

## history

All transfers in and out of a given wallet.

# Creation

## new\_coldkey

Creates a new coldkey in the wallet.

## create

Creates a new coldkey in the wallet.

## new\_hotkey

Creates a new hotkey for a coldkey in your wallet.

## regen\_coldkey

Given a mnemonic, regenerate a coldkey.

## regen\_hotkey

Given a mnemonic, regenerate a hotkey.

## swap\_hotkey

Swap your associated hotkey.

## set\_identity

Set an identity on a coldkey. This makes your coldkey publically identifiable.  Useful for 

# Moving tao

## transfer

# security

## update

Updates the wallet security using NaCL instead of anisible vault.

# testing

## faucet

On testnet, you can add test tao to your wallet
