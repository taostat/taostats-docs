---
title: Smart Contracts with EVM
excerpt: Smart contract evaluation has launched on Bittensor.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
# Smart Contracts

Smart contracts are agreements that are codified in code.  When two (or more) parties wish to execute a smart contract, they agree on the terms, and write those terms into code - the smart contract.  Upon completion of the smart contract provisions, the contract is executed.

# EVM - Ethereum Virtual Machine

EVM is used to execute smart contracts. Generally, this is done on the ethereum blockchain, but in the case of Bittensor, these are run solely on the Bittensor subtensor chain.  It allows developers to write and deploy smart contracts in programming languages like Solidity.

It should be noted that EVM is not native to substrate blockchains (like Bittensor.). To enable EVM and smart contracts to be run on Bittensor, an EVM implementation was added.

Once you have created and compiled a smart contract, it must be deployed on the Ethereum network.

Once a contract is deployed on the subtensor, any user can call and interact with the contract.

# Executing a Smart Contract on Bittensor

A standard Bittensor wallet (your coldkey) is unable to execute smart contracts.  Your coldkey wallet is controlled on the Bittensor side of the network (you have your password and 12 word mnemonic of the Bittensor chain).

In order to create a smart contract, you must have an EVM Bittensor wallet.

## Create a Bittensor MetaMask coldkey wallet

Inside the MetaMask browser extension, create a new account.  Add a network manually:

```
Network name: "Subtensor"
New RPC URL: wss://evm.chain.opentensor.ai (wss://test.finney.opentensor.ai:443 for test)
Chain ID: 945 (This is UTF-8 encoding for Alpha character)
Currency symbol: TAO
```

# EVM wallet/ Substrate wallet interactions

With a EVM MetaMask wallet - you can execute smart contracts.  Your EVM wallet has no functionality on the Bittensor network (it cannot transfer funds, stake, etc.)

Your Bittensor wallet cannot execute smart contracts.

So how do these two types of wallets interact?

## EVM wallets on Bittensor

Your EVM wallet (in Metamask) can execute smart contracts.  It has an alias address in Bittensor that can receive funds from "regular"  Substrate wallets.  This bittensor 'alias' has no password on the Bittensor side, and cannot be used for any transactions on the Bittensor chain. Any funds that are transferred into the alias immediately appear in the EVM wallet.

<Image
  align="center"
  alt="Bittensor wallet (orange) & EVM wallet (yellow)  
The EVM wallet has a Bittensor alias for receiving funds. These will immediately appear in the EVM wallet."
  border={false}
  caption="Bittensor wallet (orange) & EVM wallet (yellow)
The EVM wallet has a Bittensor alias for receiving funds. These will immediately appear in the EVM wallet."
  src="https://files.readme.io/f3abfc30d2d41293749141a941d9d8f3e243b7c00613638ebc9b2ddc16d25194-image.png"
/>

### Bittensor wallets on EVM

In a similar way, Bittensor wallets have an alias address on EVM that can receive funds. This EVM 'alias' has no password and cannot be used to execute smart contracts on EVM, but can receive transfers or the execution of smart contracts.

<Image align="center" alt="EVM wallet (yellow) can transfer funds to the Bittensor wallet alias. This appears in the Bittensor wallet immediately." border={false} caption="EVM wallet (yellow) can transfer funds to the Bittensor wallet alias. This appears in the Bittensor wallet immediately." src="https://files.readme.io/6ab8172063c03ab1d2a966a1cc9fcd84a5272e4a41f7e1d873bec35ce3b8ea82-image.png" />

<Image align="center" alt="EVM wallet executes a smart contract, and the Bittensor wallet's alias receives the funds as a result of the execution." border={false} caption="EVM wallet executes a smart contract, and the Bittensor wallet's alias receives the funds as a result of the execution. These funds appear in the Bittensor wallet upon execution of the contract." src="https://files.readme.io/3db4f59dd03e01bd9d960922f1d3091bf290d670966449ac6c32e0af2da25833-image.png" />

<br />

> 📘 1 tao = 1e18 in Bittensor EVM.
>
> Due to the precision of token in EVM, 1 tao is written as (1 billion)^2.

# Creating and executing Smart Contracts

the Opentensor Foundation has up to date guides on running smart contracts on Bittensor:

[https://docs.bittensor.com/evm-tutorials/](https://docs.bittensor.com/evm-tutorials/)

# Contract verification

(from our friends at [Taonado](https://github.com/taonado/taonado-cash/blob/main/verify-contract.md) 

To verify the source code for a deployed contract on the taostats evm explorer. See hardhat.config.ts for configuration. This does not require a valid config.ts setup with keys etc..

```pnpm hardhat verify --network taostats 0xDEPLOYED_CONTRACT_ADDRESS "CONSTRUCTOR_PARAM_0" "CONSTRUCTOR_PARAM_1"```


If you run into issues verifying, it is likely an issue with the `@openzeppelin/hardhat-upgrades` package changes to how contracts are tested before verified. There is a compatibility issue with Blockscout. In particular, [HardhatError HH110](https://v2.hardhat.org/hardhat-runner/docs/errors#HH110) : Invalid JSON-RPC response is possible with error: "Action not found."

To fix this, you have to temporarily uninitialize the @openzeppelin/hardhat-upgrades package for the purposes of verifying any contract, which will run the expected verify method which works with Blockscout's RPC.

Root cause is the @openzeppelin/hardhat-upgrades package checks if the address isBeacon by trying to get the implementation() address which the Blockscout eth-RPC returns an error message different than what is expected by the lib, so it incorrectly assumes there is an RPC issue.
