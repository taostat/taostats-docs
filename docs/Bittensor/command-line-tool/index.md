---
title: Command Line Interface (CLI)
excerpt: CLI or clee?
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
The Bittensor command line interface (CLI) allows programmatic access to the Bittensor ecosystem.  As of September 2024, the BTCLI has is no longer part of the Bittensor package and is a standalone app. 

# Installation

## From Source

As of release 8.0.0 (September 2024), the btcli has its own repository separate from the SDK.

```
git clone https://github.com/opentensor/btcli.git
cd btcli
pip install .
```

## From pip

```
pip install bittensor-cli
```

If you would like the SDK and the CLI:

```
pip install bittensor[cli] #for sdk + cli
```

Trouble?  The most up-to-date instructions can be found in the [Bittensor documentation](https://docs.bittensor.com/btcli). 

# Using the CLI

To get all of the latest commands from the CLI use `btcli --help`:

```shell
btcli --help

Usage: btcli [OPTIONS] COMMAND [ARGS]...                                                                                                                              
                                                                                                                                                                       
 Command line interface (CLI) for Bittensor. Uses the values in the configuration file. These values can be overriden by passing them explicitly in the command line.  
                                                                                                                                                                       
╭─ Options ───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ --version                                                                                                                                                           │
│ --install-completion          Install completion for the current shell.                                                                                             │
│ --show-completion             Show completion for the current shell, to copy it or customize the installation.                                                      │
│ --help                        Show this message and exit.                                                                                                           │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
╭─ Commands ──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ config    Config commands, aliases: `c`, `conf`                                                                                                                     │
│ root      Root commands, alias: `r`                                                                                                                                 │
│ stake     Stake commands, alias: `st`                                                                                                                               │
│ subnets   Subnets commands, alias: `s`, `subnet`                                                                                                                    │
│ sudo      Sudo commands, alias: `su`                                                                                                                                │
│ wallet    Wallet commands, aliases: `wallets`, `w`                                                                                                                  │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
                                                                                                                                                                       
 Made with ❤ by The Openτensor Foundaτion     
```

# Configuring the CLI

The new `btcli config` allows you to set default parameters on your installation.
