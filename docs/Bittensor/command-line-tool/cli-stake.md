---
title: 'CLI: Stake'
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
```
 btcli st --help
                                                                                                                                                                       
 Usage: btcli st [OPTIONS] COMMAND [ARGS]...                                                                                                                           
                                                                                                                                                                       
╭─ Options ───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ --help          Show this message and exit.                                                                                                                         │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
╭─ Stake Management ──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ add      Stake TAO to one or more hotkeys associated with the user's coldkey.                                                                                       │
│ remove   Unstake TAO from one or more hotkeys and transfer them back to the user's coldkey.                                                                         │
│ show     Lists all the stake accounts associated with a user's wallet.                                                                                              │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
╭─ Child Hotkeys ─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ child    Child Hotkey commands, alias: `children`                                                                                                                   │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
                                                                                                                                                                       
 Made with ❤ by The Openτensor Foundaτion                    
```

# Manage your stake

<br />

# add

 Stake TAO to a validator.

```shell
btcli st add
Enter the netuid to use. Leave blank for all netuids: 1
Enter the wallet name (rao): 
Enter the wallet hotkey name or ss58 address to stake to (or Press Enter to view delegates): 



                                                       Subnet 1: alpha                                                        
                                                        Network: test                                                         
                                                                                                                              
  # ┃ UID ┃ Stake (α) ┃ Alpha (α) ┃  Tao (τ) ┃ Dividends ┃ Incentive ┃ Emissions (α) ┃ Hotkey ┃ Coldkey ┃ Identity            
━━━━╇━━━━━╇━━━━━━━━━━━╇━━━━━━━━━━━╇━━━━━━━━━━╇━━━━━━━━━━━╇━━━━━━━━━━━╇━━━━━━━━━━━━━━━╇━━━━━━━━╇━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━
  1 │ 77  │  23.34k α │  23.12k α │ τ 220.35 │  0.00490  │  0.0098   │   0.40196 α   │ 5Grwva │ 5CwgoT  │ (*Owner controlled) 
  2 │ 96  │  23.34k α │  23.12k α │ τ 220.35 │  0.00490  │  0.0098   │   0.40196 α   │ 5Grwva │ 5CwgoT  │ (*Owner controlled) 
  3 │ 81  │  76.45k α │  68.15k α │  τ 8.30k │  0.50000  │  0.0000   │  41.00023 α   │ 5FCPTn │ 5D2d3Y  │ ~                   
  4 │ 78  │  34.11k α │  34.11k α │   τ 1.36 │  0.00490  │  0.0098   │   0.40196 α   │ 5FHneW │ 5CwgoT  │ ~                   
  5 │  6  │   9.15k α │   9.00k α │ τ 151.01 │  0.00490  │  0.0098   │   0.40196 α   │ 5C86aJ │ 5GeYLB  │ Owner10             
  6 │ 22  │   2.26k α │  452.40 α │  τ 1.80k │  0.00490  │  0.0098   │   0.40196 α   │ 5DHsdG │ 5Csxoe  │ ~                   
  7 │ 100 │  844.39 α │  844.39 α │   τ 0.00 │  0.00490  │  0.0098   │   0.40196 α   │ 5CtaFa │ 5H13H4  │ ~                   
  8 │ 24  │  750.34 α │  750.31 α │   τ 0.03 │  0.00490  │  0.0098   │   0.40196 α   │ 5Dqbne │ 5EHVUN  │ ~                   
  9 │ 72  │  702.69 α │  700.69 α │   τ 2.00 │  0.00490  │  0.0098   │   0.40196 α   │ 5H6V38 │ 5FUcd4  │ ~                   
 10 │  1  │  693.55 α │  453.75 α │ τ 239.80 │  0.00490  │  0.0098   │   0.40196 α   │ 5ETsfk │ 5Ebtu6  │ ~                   
 11 │  5  │  683.69 α │  431.13 α │ τ 252.56 │  0.00490  │  0.0098   │   0.40196 α   │ 5DXqvJ │ 5CS1kB  │ ~                   
 12 │  2  │  662.54 α │  431.13 α │ τ 231.41 │  0.00490  │  0.0098   │   0.40196 α   │ 5FFXcJ │ 5Hh8CT  │ ~                   
────┼─────┼───────────┼───────────┼──────────┼───────────┼───────────┼───────────────┼────────┼─────────┼─────────────────────
    │     │ 212.75k α │ 200.44k α │ 12.31k α │   1.000   │           │   82.0005 α‎   │        │         │                     

Enter the number of the delegate you want to stake to (or press Enter to cancel) (): 3

Selected delegate: 5FCPTnjevGqAuTttetBy4a24Ej3pH9fiQ8fmvP1ZkrVsLUoT
                                                                                                                                         
                                                 Wallet Coldkey Balance                                                                  
                                                     Network: test                                                                       
    Wallet Name     Coldkey Address                                    Free Balance   Staked Balance   Total Balance                     
    ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━                     
    rao             5FNqfWE5DvzHiUZqyep3Bt4M9c5W3TTwu1PwDdbehYn17AwZ       τ 0.5000         τ 2.9861        τ 3.4861                     
                                                                                                                                         
                                                                                                                                         
                                                                                                                                         
    Total Balance                                                          τ 0.5000         τ 2.9861        τ 3.4861                     
    ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━                     
                                                                                                                                         
Amount to stake (TAO τ): 0.5

```

The CLI prompts you on slippage

```
                                                      Staking to:                                                      
                      Wallet: rao, Coldkey ss58: 5FNqfWE5DvzHiUZqyep3Bt4M9c5W3TTwu1PwDdbehYn17AwZ                      
                                                     Network: test                                                     
                                                                                                                       
 Netuid ┃                      Hotkey                      ┃ Amount (τ) ┃      Rate (per τ)      ┃ Received ┃ Slippage 
━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━╇━━━━━━━━━━
   1    │ 5FCPTnjevGqAuTttetBy4a24Ej3pH9fiQ8fmvP1ZkrVsLUoT │  τ 0.5000  │ 5.710095678705798 α/τ  │ 2.8549 α‎ │ 0.0037 % 
────────┼──────────────────────────────────────────────────┼────────────┼────────────────────────┼──────────┼──────────
        │                                                  │            │                        │          │          

Description:
The table displays information about the stake operation you are about to perform.
The columns are as follows:
    - Netuid: The netuid of the subnet you are staking to.
    - Hotkey: The ss58 address of the hotkey you are staking to. 
    - Amount: The TAO you are staking into this subnet onto this hotkey.
    - Rate: The rate of exchange between your TAO and the subnet's stake.
    - Received: The amount of stake you will receive on this subnet after slippage.
    - Slippage: The slippage percentage of the stake operation. (0% if the subnet is not dynamic i.e. root).


Would you like to continue? [y/n]: y
Enter your password: 
Decrypting...
Balance:
  τ 0.5000 ➡ τ 0.0000
Subnet: 1 Stake:
  189.4697 α‎ ➡ 192.3218 α‎

```

<br />

## list

```
btcli stake show
Enter the wallet name or coldkey ss58 address (rao): 
                                                                                                      
                       Hotkey: 5FCPTnjevGqAuTttetBy4a24Ej3pH9fiQ8fmvP1ZkrVsLUoT                       
                                            Network: test                                             
                                                                                                      
                             See below for an explanation of the columns                              
                                                                                                      
        ┃           ┃     Value ┃           ┃    Price    ┃                  ┃            ┃  Emission 
 Netuid ┃ Name      ┃ (α x τ/α) ┃ Stake (α) ┃ (τ_in/α_in) ┃    Swap (α -> τ) ┃ Registered ┃ (α/block) 
━━━━━━━━╇━━━━━━━━━━━╇━━━━━━━━━━━╇━━━━━━━━━━━╇━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━╇━━━━━━━━━━━
 0      │ τ tau     │    τ 0.50 │  τ‎ 0.50   │ 1.0000 τ/τ‎  │     N/A (0.000%) │        YES │  τ 0.0000 
 1      │ α‎ alpha   │   τ 33.68 │ 192.32 α‎  │ 0.1751 τ/α‎  │ τ 33.60 (0.247%) │        YES │  0.4141 α‎ 
 19     │ t‎ tau     │    τ 0.64 │ 637.01 t‎  │ 0.0010 τ/t‎  │  τ 0.64 (0.434%) │        YES │  0.8283 t‎ 
 5      │ ε‎ epsilon │    τ 0.62 │ 366.31 ε‎  │ 0.0017 τ/ε‎  │  τ 0.62 (0.256%) │        YES │  0.8283 ε‎ 
────────┼───────────┼───────────┼───────────┼─────────────┼──────────────────┼────────────┼───────────
 4      │           │   τ 35.45 │           │             │          τ 35.36 │            │           

Press Enter to continue to the next hotkey...

                                                                                                     
                      Hotkey: 5Gzx1P8s3Pq9jTpYFzsGpTCzhBpwUuT4sAX4Rhc78QuodsRz                       
                                            Network: test                                            
                                                                                                     
                             See below for an explanation of the columns                             
                                                                                                     
        ┃           ┃     Value ┃           ┃    Price    ┃                 ┃            ┃  Emission 
 Netuid ┃ Name      ┃ (α x τ/α) ┃ Stake (α) ┃ (τ_in/α_in) ┃   Swap (α -> τ) ┃ Registered ┃ (α/block) 
━━━━━━━━╇━━━━━━━━━━━╇━━━━━━━━━━━╇━━━━━━━━━━━╇━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━╇━━━━━━━━━━━
 281    │ ऋ‎ DogeTAO │   τ 10.55 │ 694.95 ऋ‎  │ 0.0152 τ/ऋ‎  │ τ 9.50 (9.998%) │        YES │  0.7519 ऋ‎ 
────────┼───────────┼───────────┼───────────┼─────────────┼─────────────────┼────────────┼───────────
 1      │           │   τ 10.55 │           │             │          τ 9.50 │            │           



Wallet:
  Coldkey SS58: 5FNqfWE5DvzHiUZqyep3Bt4M9c5W3TTwu1PwDdbehYn17AwZ
  Free Balance: τ 0.0000
  Total TAO (τ): τ 16.96
  Total Value (τ): τ 46.00

```

Enter your wallet name to display all of the hotkeys that have tao delegated to them.  This will include all active validators and miners.

<br />

# remove

Remove stake from a hotkey. 

```
btcli st remove
Enter the netuid to use. Leave blank for all netuids: 1
Enter the wallet name (rao): 
Enter the hotkey name or ss58 address to unstake from (or Press Enter to view existing staked hotkeys): 


                                                                               
                       Hotkeys with Stakes for Subnet 1                        
                                                                               
 Index ┃ Identity ┃ Netuids ┃ Hotkey Address                                   
━━━━━━━╇━━━━━━━━━━╇━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
     0 │ ~        │ 1       │ 5FCPTnjevGqAuTttetBy4a24Ej3pH9fiQ8fmvP1ZkrVsLUoT 
───────┼──────────┼─────────┼──────────────────────────────────────────────────
       │          │         │                                                  

Enter the index of the hotkey you want to unstake from [0]: 0
Tip: Enter 'q' any time to skip further entries and process existing unstakes
Unstake all: 192.3218 α‎ from ~ on netuid: 1?  [y/n/q] (n): n
Enter amount to unstake in α from subnet: 1 (Max: 192.3218 α‎): .000001
                                                                           
                               Unstaking to:                               
Wallet: rao, Coldkey ss58: 5FNqfWE5DvzHiUZqyep3Bt4M9c5W3TTwu1PwDdbehYn17AwZ
                               Network: test                               
                                                                           
 Netuid ┃ Hotkey ┃ Amount (α) ┃    Rate (τ/α)    ┃ Received (τ) ┃ Slippage 
━━━━━━━━╇━━━━━━━━╇━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━╇━━━━━━━━━━
   1    │   ~    │  0.0000 α‎  │ 0.175136674(τ/α) │   τ 0.0000   │ 0.0000 % 
────────┼────────┼────────────┼──────────────────┼──────────────┼──────────
        │        │            │                  │   τ 0.0000   │          

Description:
The table displays information about the stake remove operation you are about to perform.
The columns are as follows:
    - Netuid: The netuid of the subnet you are unstaking from.
    - Hotkey: The ss58 address or identity of the hotkey you are unstaking from. 
    - Amount: The stake amount you are removing from this key.
    - Rate: The rate of exchange between TAO and the subnet's stake.
    - Received: The amount of free balance TAO you will receive on this subnet after slippage.
    - Slippage: The slippage percentage of the unstake operation. (0% if the subnet is not dynamic i.e. root).


```