---
title: 'CLI: Wallet'
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
Actions around your Bittensor wallet.

```
btcli wallet
Error: the following arguments are required: subcommand
usage: btcli <command> <command args> wallet [-h]
                                             {list,overview,transfer,inspect,balance,create,new_hotkey,new_coldkey,regen_coldkey,regen_coldkeypub,regen_hotkey,faucet,update,swap_hotkey,set_identity,get_identity,history}
                                             ...

positional arguments:
  {list,overview,transfer,inspect,balance,create,new_hotkey,new_coldkey,regen_coldkey,regen_coldkeypub,regen_hotkey,faucet,update,swap_hotkey,set_identity,get_identity,history}
                        Commands for managing and viewing wallets.
    list                List wallets
    overview            Show registered account overview.
    transfer            Transfer Tao between accounts.
    inspect             Inspect a wallet (cold, hot) pair
    balance             Checks the balance of the wallet.
    create              Creates a new coldkey (for containing balance) under the specified path.
    new_hotkey          Creates a new hotkey (for running a miner) under the specified path.
    new_coldkey         Creates a new coldkey (for containing balance) under the specified path.
    regen_coldkey       Regenerates a coldkey from a passed value
    regen_coldkeypub    Regenerates a coldkeypub from the public part of the coldkey.
    regen_hotkey        Regenerates a hotkey from a passed mnemonic
    faucet              Perform PoW to receieve test TAO in your wallet.
    update              Updates the wallet security using NaCL instead of anvisible vault.
    swap_hotkey         Swap your associated hotkey.
    set_identity        Create or update identity on-chain for a given cold wallet. Must be a subnet owner.
    get_identity        Creates a new coldkey (for containing balance) under the specified path.
    history             Fetch transfer history associated with the provided wallet

options:
  -h, --help            show this help message and exit
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
