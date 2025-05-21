---
title: 'CLI: Root'
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
The root command provides a number of actions:

```
btcli root --help
                                                                                                                                                                       
 Usage: btcli root [OPTIONS] COMMAND [ARGS]...                                                                                                                         
                                                                                                                                                                       
╭─ Options ───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ --help          Show this message and exit.                                                                                                                         │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
╭─ Commands ──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ list               Show the neurons (root network validators) in the root network (netuid = 0).                                                                     │
│ register           Register a neuron (a subnet validator or a subnet miner) to a specified subnet by recycling some TAO to cover for the registration cost.         │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
╭─ Weights Management ────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ boost              Increase (boost) the weights for a specific subnet in the root network. Any amount provided will be added to the subnet's existing weight.       │
│ get-weights        Shows a table listing the weights assigned to each subnet in the root network.                                                                   │
│ set-weights        Set the weights for different subnets, by setting them in the root network.                                                                      │
│ slash              Decrease (slash) the weights for a specific subnet in the root network. Any amount provided will be subtracted from the subnet's existing        │
│                    weight.                                                                                                                                          │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
╭─ Delegation ────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ delegate-stake     Stakes TAO to a specified delegate hotkey.                                                                                                       │
│ list-delegates     Displays a table of Bittensor network-wide delegates, providing a comprehensive overview of delegate statistics and information.                 │
│ my-delegates       Shows a table with the details on the user's delegates.                                                                                          │
│ set-take           Allows users to change their delegate take percentage.                                                                                           │
│ undelegate-stake   Allows users to withdraw their staked TAO from a delegate.                                                                                       │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
╭─ Governance ────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ nominate           Enables a wallet's hotkey to become a delegate.                                                                                                  │
│ proposals          View active proposals for the senate in the Bittensor's governance protocol.                                                                     │
│ senate             Shows the Senate members of the Bittensor's governance protocol.                                                                                 │
│ senate-vote        Cast a vote on an active proposal in Bittensor's governance protocol.                                                                            │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
                                                                                                                                                                       
 Made with ❤ by The Openτensor Foundaτion                                                                       
```

# Commands

## List

```
Show the neurons (root network validators) in the root network (netuid = 0).                                                                                          
 USAGE                                                                                                                                                                 
                                                                                                                                                                       
 The command fetches and lists the neurons (root network validators) in the root network, showing their unique identifiers (UIDs), names, addresses, stakes, and       
 whether they are part of the senate (network governance body).                                                                                                        
                                                                                                                                                                       
 This command is useful for understanding the composition and governance structure of the Bittensor network's root network. It provides insights into which neurons    
 hold significant influence and responsibility within the Bittensor network.                                                                                           
                                                                                                                                                                       
 EXAMPLE                                                                                                                                                               
                                                                                                                                                                       
 $ btcli root list                                                                                                                                                     
                                                                                                                                                                       
╭─ Options ───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ --network,--subtensor.network             TEXT  The subtensor network to connect to. Default: finney. Allowed values: local, test, finney.                          │
│ --chain,--subtensor.chain_endpoint        TEXT  The subtensor chain endpoint URL to connect to. The format should be similar to: ws://127.0.0.1:9946.               │
│ --quiet                                         Display only critical information on the console.                                                                   │
│ --verbose                                       Enable verbose output.                                                                                              │
│ --help                                          Show this message and exit.                                                                                         │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯

```

```
                                                     Root Network                                                     
                                                    Network finney                                                    
 UID ┃ NAME                            ┃ ADDRESS                                          ┃        STAKE(τ) ┃ SENATOR 
━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━╇━━━━━━━━━
 2   │ Openτensor Foundaτion           │ 5F4tQyWrhfGVcNhoqeiNsR6KjD4wMZ2kfhLj4oHYuyHbZAc3 │    879208.10926 │ Yes     
     │                                 │                                                  │                 │         
 6   │ Taostats & Corcel               │ 5GKH9FPPnWSUoeeTJp19wVtd84XqFW4pyK2ijV2GsFbhTrP1 │    812123.86617 │ Yes     
     │                                 │                                                  │                 │         
 15  │ Owl Ventures                    │ 5CsvRJXuR955WojnGMdok1hbhffZyB4N5ocrv82f3p5A2zVp │    584420.88303 │ No      
     │                                 │                                                  │                 │         
 20  │ Yuma, a DCG Company             │ 5HEo565WAy4Dbq3Sv271SAi7syBSofyfhhwRNjFNSM2gP9M2 │    576217.73960 │ Yes     
     │                                 │                                                  │                 │         
 61  │ Datura                          │ 5GP7c3fFazW9GXK8Up3qgu2DJBk8inu4aK9TZy3RuoSWVCMi │    342329.61221 │ Yes     
     │                                 │                                                  │                 │         
 4   │ Bittensor Guru                  │ 5HK5tp6t2S59DywmHRWPBVJeJ86T61KjurYqeooqj8sREpeN │    298713.69429 │ Yes     
     │                                 │                                                  │                 │         
 29  │ Crucible Labs                   │ 5HYk8DMKWK8TJyPzZJ9vmZk7B5NPCgjnZoyZ1ZsB54RXdN47 │    285380.88046 │ No      

```

## Register

Register a neuron on the root network.

```
Register a neuron (a subnet validator or a subnet miner) to a specified subnet by recycling some TAO to cover for the registration cost.                              
 This command adds a new neuron (a subnet validator or a subnet miner) to a specified subnet, contributing to the decentralization and robustness of Bittensor.        
                                                                                                                                                                       
 # Usage:                                                                                                                                                              
                                                                                                                                                                       
 Before registering, the command checks if the specified subnet exists and whether the TAO balance in the user's wallet is sufficient to cover the registration cost.  
 The registration cost is determined by the current recycle amount for the specified subnet. If the balance is insufficient or the subnet does not exist, the command  
 will exit with an appropriate error message.                                                                                                                          
                                                                                                                                                                       
 # Example usage:                                                                                                                                                      
                                                                                                                                                                       
 $ btcli subnets register --netuid 1                                                                                                                                   
                                                                                                                                                                       
╭─ Options ───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ --network,--subtensor.network                                                                    TEXT  The subtensor network to connect to. Default: finney.        │
│                                                                                                        Allowed values: local, test, finney.                         │
│ --chain,--subtensor.chain_endpoint                                                               TEXT  The subtensor chain endpoint URL to connect to. The format   │
│                                                                                                        should be similar to: ws://127.0.0.1:9946.                   │
│ --wallet-name,--name,--wallet_name,--wallet.name                                                 TEXT  Name of the wallet. [default: None]                          │
│ --wallet-path,--wallet_path,--wallet.path                 -p                                     TEXT  Path where the wallets are located. For example:             │
│                                                                                                        `/Users/btuser/.bittensor/wallets`.                          │
│                                                                                                        [default: None]                                              │
│ --hotkey,--wallet_hotkey,--wallet-hotkey,--wallet.hotkey  -H                                     TEXT  Hotkey of the wallet [default: None]                         │
│ --prompt,--prompt                                             --no-prompt,--yes,--no_prompt  -y        Enable or disable interactive prompts. [default: prompt]     │
│ --quiet                                                                                                Display only critical information on the console.            │
│ --verbose                                                                                              Enable verbose output.                                       │
│ --help                                                                                                 Show this message and exit.                                  │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯

```

# Weights Management

Validators on the root subnet assign weights to each subnet. These commands are used to edit these weights.

## Boost

Increase (boost) the weights for a specific subnet in the root network. Any amount provided will be added to the subnet's existing weight.

```
btcli root boost --help
                                                                                                                                                                       
 Usage: btcli root boost [OPTIONS]                                                                                                                                     
                                                                                                                                                                       
 Increase (boost) the weights for a specific subnet in the root network. Any amount provided will be added to the subnet's existing weight.                            
 EXAMPLE                                                                                                                                                               
                                                                                                                                                                       
 $ btcli root boost --netuid 1 --increase 0.01                                                                                                                         
                                                                                                                                                                       
╭─ Options ───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ --network,--subtensor.network                                                                    TEXT     The subtensor network to connect to. Default: finney.     │
│                                                                                                           Allowed values: local, test, finney.                      │
│ --chain,--subtensor.chain_endpoint                                                               TEXT     The subtensor chain endpoint URL to connect to. The       │
│                                                                                                           format should be similar to: ws://127.0.0.1:9946.         │
│ --wallet-name,--name,--wallet_name,--wallet.name                                                 TEXT     Name of the wallet. [default: None]                       │
│ --wallet-path,--wallet_path,--wallet.path                 -p                                     TEXT     Path where the wallets are located. For example:          │
│                                                                                                           `/Users/btuser/.bittensor/wallets`.                       │
│                                                                                                           [default: None]                                           │
│ --hotkey,--wallet_hotkey,--wallet-hotkey,--wallet.hotkey  -H                                     TEXT     Hotkey of the wallet [default: None]                      │
│ --netuid                                                                                         INTEGER  The netuid of the subnet in the root network, (e.g. 1).   │
│                                                                                                           [default: None]                                           │
│ --amount,--increase                                       -a                                     FLOAT    Amount (float) to boost (added to the existing weight),   │
│                                                                                                           (e.g. 0.01)                                               │
│                                                                                                           [default: None]                                           │
│ --prompt,--prompt                                             --no-prompt,--yes,--no_prompt  -y           Enable or disable interactive prompts. [default: prompt]  │
│ --quiet                                                                                                   Display only critical information on the console.         │
│ --verbose                                                                                                 Enable verbose output.                                    │
│ --help                                                                                                    Show this message and exit.                               │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯


```

## get-weights

A gigantic table of all the weights set on the root subnet

```
btcli root  get-weights   --help
                                                                                                                                                                       
 Usage: btcli root get-weights [OPTIONS]                                                                                                                               
                                                                                                                                                                       
 Shows a table listing the weights assigned to each subnet in the root network.                                                                                        
 This command provides visibility into how network responsibilities and rewards are distributed among various subnets. This information is crucial for understanding   
 the current influence and reward distribution across different subnets. Use this command if you are interested in the governance and operational dynamics of the      
 Bittensor network.                                                                                                                                                    
                                                                                                                                                                       
 EXAMPLE                                                                                                                                                               
                                                                                                                                                                       
 $ btcli root get_weights                                                                                                                                              
  
```

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/714681824f63af1f27851754090c8f497dfb84c5824dacb1e355d355e6a63a76-image.png",
        null,
        "Welcome to the matrix."
      ],
      "align": "center",
      "caption": "Welcome to the matrix."
    }
  ]
}
[/block]


## set-weights

For root validators to set subnet weights.

```
Usage: btcli root set-weights [OPTIONS]                                                                                                                               
                                                                                                                                                                       
 Set the weights for different subnets, by setting them in the root network.                                                                                           
 To use this command, you should specify the netuids and corresponding weights you wish to assign. This command is used by network senators to influence the           
 distribution of subnet rewards and responsibilities.                                                                                                                  
                                                                                                                                                                       
 You must have a comprehensive understanding of the dynamics of the subnets to use this command. It is a powerful tool that directly impacts the subnet's  operational 
 mechanics and reward distribution.                                                                                                                                    
                                                                                                                                                                       
 EXAMPLE                                                                                                                                                               
                                                                                                                                                                       
 With no spaces between the passed values:                                                                                                                             
                                                                                                                                                                       
 $ btcli root set-weights --netuids 1,2 --weights 0.2,0.3                                                                                                              
                                                                                                                                                                       
 or                                                                                                                                                                    
                                                                                                                                                                       
 Include double quotes to include spaces between the passed values:                                                                                                    
                                                                                                                                                                       
 $ btcli root set-weights --netuids "1, 2" --weights "0.2, 0.3"          
```

## Slash

```
Usage: btcli root slash [OPTIONS]                                                                                                                                     
                                                                                                                                                                       
 Decrease (slash) the weights for a specific subnet in the root network. Any amount provided will be subtracted from the subnet's existing weight.                     
 EXAMPLE                                                                                                                                                               
                                                                                                                                                                       
 $ btcli root slash --netuid 1 --decrease 0.01                                                                                                                         
                                                      
```

<br />

## delegate-stake

Delegate stake to a validator

```
Stakes TAO to a specified delegate hotkey.                                                                                                                            
 This command allocates the user's TAO to the specified hotkey of a delegate, potentially earning staking rewards in return. If the                                    
 `--all` flag is used, it delegates the entire TAO balance available in the user's wallet.                                                                             
                                                                                                                                                                       
 This command should be run by a TAO holder. Compare this command with "btcli stake add" that is typically run by a subnet validator to add stake to their own         
 delegate hotkey.                                                                                                                                                      
                                                                                                                                                                       
 EXAMPLE                                                                                                                                                               
                                                                                                                                                                       
 $ btcli root delegate-stake --delegate_ss58key <SS58_ADDRESS> --amount <AMOUNT>                                                                                       
                                                                                                                                                                       
 $ btcli root delegate-stake --delegate_ss58key <SS58_ADDRESS> --all                                                                                                   
                                                                                                                                                                       
 Note: This command modifies the blockchain state and may incur transaction fees. The user should ensure the delegate's address and the amount to be staked are        
 correct before executing the command.                    
```

## list-delegates

Lists the delegates on the root subnet. Can be filtered with --wallet-name to show delegators for a specific wallet

## my-delegates

Lists delegates of a specific wallet.

## set-take

For validators to set their take.  Take is the percentage of validator emission returned to the validator

```
 Allows users to change their delegate take percentage.                                                                                                                
 This command can be used to update the delegate takes individually for every subnet. To run the command, the user must have a configured wallet with both hotkey and  
 coldkey. The command performs the below checks:                                                                                                                       
                                                                                                                                                                       
     1. The provided hotkey is already a delegate.                                                                                                                     
     2. The new take value is within 0-18% range.                                                                                                                      
                                                                                                                                                                       
 EXAMPLE                                                                                                                                                               
                                                                                                                                                                       
 $ btcli root set_take --wallet-name my_wallet --wallet-hotkey my_hotkey         
```

## undelegate-stake

```
 Allows users to withdraw their staked TAO from a delegate.                                                                                                            
 The user must provide the delegate hotkey's ss58 address and the amount of TAO to undelegate. The function will then send a transaction to the blockchain to process  
 the undelegation. This command can result in a change to the blockchain state and may incur transaction fees.                                                         
                                                                                                                                                                       
 EXAMPLE                                                                                                                                                               
                                                                                                                                                                       
 $ btcli undelegate --delegate_ss58key <SS58_ADDRESS> --amount <AMOUNT>                                                                                                
                                                                                                                                                                       
 $ btcli undelegate --delegate_ss58key <SS58_ADDRESS> --all       
```

# Governance

## Nominate

Nominate your hotkey to be a member of the Bittensor senate.

## Proposals

 View active proposals for the senate in the Bittensor's governance protocol.  
 This command displays the details of ongoing proposals, including proposal hashes, votes, thresholds, and proposal data.

## senate

 Shows the Senate members of the Bittensor's governance protocol.  
 This command lists the delegates involved in the decision-making process of the Bittensor network, showing their names and wallet addresses. This information is  
 crucial for understanding who holds governance roles within the network.

## senate-vote

This command is used by Senate members to vote on various proposals that shape the network's future. Use `btcli root proposals` to see the active proposals and their  
 hashes.                                                                                                                                                               

 USAGE                                                                                                                                                                 

 The user must specify the hash of the proposal they want to vote on. The command then allows the Senate member to cast a 'Yes' or 'No' vote, contributing to the  
 decision-making process on the proposal. This command is crucial for Senate members to exercise their voting rights on key proposals. It plays a vital role in the  
 governance and evolution of the Bittensor network.