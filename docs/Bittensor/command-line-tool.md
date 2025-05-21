---
title: Command Line Interface (CLI)
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
The Bittensor command line interface (CLI) allows programmatic access to the Bittensor ecosystem.

# Installing the CLI

The CLI is part of the Bittensor package.

The most up-to-date instructions can be found in the [Bittensor documentation](https://docs.bittensor.com/getting-started/installation). 

# Using the CLI

To get all of the latest commands from the CLI:

```shell
btcli --help

usage: btcli <command> <command args>

bittensor cli v6.6.0

positional arguments:
  {subnets,s,subnet,root,r,roots,wallet,w,wallets,stake,st,stakes,sudo,su,sudos,legacy,l,info,i}
    subnets (s, subnet)
                        Commands for managing and viewing subnetworks.
    root (r, roots)     Commands for managing and viewing the root network.
    wallet (w, wallets)
                        Commands for managing and viewing wallets.
    stake (st, stakes)  Commands for staking and removing stake from hotkey accounts.
    sudo (su, sudos)    Commands for subnet management
    legacy (l)          Miscellaneous commands.
    info (i)            Instructions for enabling autocompletion for the CLI.

options:
  -h, --help            show this help message and exit
  --print-completion {bash,zsh,tcsh}
                        Print shell tab completion script
```

# [subnets](doc:btcli-subnets): Commands related to subnets

- [Informational](doc:btcli-subnets#informational)
- [subnet owners](doc:btcli-subnets#subnet-owners)
- [miners and validators](doc:btcli-subnets#miners-and-validators)

# [stake](doc:cli-stake): Add and remove stake from hotkeys

# [wallet](doc:cli-wallet): Work with your Bittensor wallets

# [sudo](doc:cli-sudo): Set and query subnet parameters

# [root](doc:cli-root): Parameters for members of the root subnet 

# legacy: Deprecated

# info: Instructions on autocompletion of CLI