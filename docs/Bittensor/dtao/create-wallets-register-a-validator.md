---
title: Create Wallets & Register a Subnet
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
> 📘 This page assumes that you have already completed the steps to [Deploy a Bittensor-Rao Chain](doc:deploy-a-dtao-chain) on your local machine, or are running on raonet.

# Creating Wallets, Hotkeys and obtaining tao

Ok - now we have everything up and running to play with dtao.  You'll want a few test wallets with a few hotkeys each.  If you are familiar with bittensor, you already know the commands needed:

```shell
btcli w new_coldkey
btcli w new_hotkey
```

Follow the steps to create a coldkey (or two) and add a few hotkeys to each coldkey.

You'll need some tao in your coldkeys.  Since it is a local network, there is a faucet:

```shell
btcli w faucet --subtensor.network local --wallet.name <your wallet name>
```

This will add 3,000 tao to your wallet.  Repeat as needed across your coldkeys.

> 📘 When making btcli commands, the default is to connect to the finney network (production chain)
> 
> To test your local chain, add:  
> `--subtensor.network local`
> 
> The bittensor version for raonet defaults to `--subtensor.network raonet`

# Register a subnet

To begin, you'll need to register a subnet or two:

```
btcli s create --subtensor.network local --wallet.name <walletname?
```

# Add stake to a subnet

Use `btcli s show` to find a validator on the subnet that you wish to stake to:

```
btcli st add --subtensor.network local --netuid 1 --wallet.name <walletname>
Enter staking hotkey name or ss58_address (default): <the hotkey>
```

Slippage is the amount of the tao that you will immediately lost by completing the transfer. Smaller transfers (as a percentage of tao staked to the subnet) have lower slippage.

```
Stake all: τ1,998.0000? [y/n]: n
Enter amount to stake in τ: 500
                                      Add Stake: 5Dt17kKyhC4pnrJuWtmFYucC7hfr3g2q5QYFZkoTHKg8ZZtr                                       
    netuid    ┃      hotkey       ┃     amount (τ)     ┃              rate (α/τ)               ┃     received (α)      ┃    slippage    
━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━
      1       │     5Dj...jjZ     │     τ500.0000      │        1.074476704889997(α/τ)         │       523.0584α‎       │    2.6394 %    
──────────────┼───────────────────┼────────────────────┼───────────────────────────────────────┼───────────────────────┼────────────────
              │                   │                    │                                       │                       │                
Would you like to continue? [y/n]: y
Enter password to unlock key: 

```

Choosing a different hotkey will stake on that other hotkey.