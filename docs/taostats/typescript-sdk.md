---
title: TypeScript SDK
excerpt: >-
  Are you a TypeScript developer using our APIs?  Our SDK might slimplify
  things!
deprecated: false
hidden: false
metadata:
  robots: index
---
Our Typescript SDK is now available. It offers full access to the Taostats API, but also full customized RPC access to the Bittensor chain.

IN addition to making calls to Taostats, you can do any transaction on the chain using the RPC nodes.

# Installation

The Taostats [TypeScript SDK](https://github.com/taostat/taostats-sdk) is available on GitHub.  The latest installation instructions can be found there.

Requirements: Node.js v 22.3.0 or higher

```shell
npm install taostats-sdk
# or
yarn add taostats-sdk
# or
pnpm add taostats-sdk
```

<br />

## Setup

the `.env` has three variables:

```
TAOSTATS_API_KEY='your-taostats-api-key'

# Only needed to interact with certain blockchain modules(stake, unstake, transfer, move) 
TAO_ACCOUNT_SEED="your twelve word seed phrase"
# OR
TAO_ACCOUNT_PRIVATE_KEY="your_private_key_in_hex"

RPC_URL="wss://your_custom_url" #Optional
```

* **TAOSTATS\_API\_KEY**: Your API key. Required to make API calls with Taostats
* **TAO\_ACCOUNT\_SEED**: Your 12 word wallet phrase.  Used for RPC calls on chain.  BE CAREFUL!  The .gitignore is properly set, but if your server is compromised, you may loose access to your wallet.
* **TAO\_ACCOUNT\_PRIVATE\_KEY**: A hex encoded version of your private key.  Used for RPC calls on chain.  BE CAREFUL!  The .gitignore is properly set, but if your server is compromised, you may loose access to your wallet.
* **RPC\_URL**: Change to run your code in testnet, or in a private node.

# Usage

## API Modules (current as of July 2, 2025)

Parameters are all identical to those in the API

<br />

* client.taoPrices - TAO price and market data endpoints
  * getTaoPrice
  * getTaoPriceHistory
  * getTaoPriceOHLC
* client.tradingView - TradingView UDF history data for subnets
  * getTradingViewHistory
* client.delegations - Delegation/staking data, slippage calculations, and stake balances
  * getSlippage
  * getDelegationEvents
  * getStakeBalanceSumInTao
  * getdTaoStakeBalance
  * getdTaoHistoricalStakeBalance
* client.accounts - Account information, balances, and transactions
  * getAccount
  * getAccountHistory
  * getTransfers
  * getOnChainIdentity
* client.chain - Blockchain data including blocks, extrinsics, events, and network statistics
  * getBlocks
  * getBlockNumbersByInterval
  * getExtrinsics
  * getEvents
  * getChainCalls
  * getLatestStats
  * getStatsHistory
  * getRuntimeVersion
  * getRuntimeVersionHistory
  * getProxyCalls
* client.subnets - Subnet data, registration, pricing, and comprehensive analytics
  * getSubnets
  * getHistoricalSubnetPricesSum
  * getLatestSubnetPricesSum
  * getSubnetRegistrations
  * getSubnetRegistrationCostHistory
  * getCurrentSubnetRegistrationCost
  * getSubnetOwner
  * getSubnetIdentity
  * getSubnetEmission
  * getSubnetsPoolsHistory
  * getCurrentSubnetPools
  * getSubnetHistory
* client.metagraph - Metagraph data including miner incentive distributions
  * getMinerIncentiveDistributionBySubnet
  * getSubnetAxonIpDistribution
  * getSubnetColdkeyDistribution
  * getLatestMinerWeight
  * getMinerWeightHistory
  * getNeuronDeregistrations
  * getNeuronRegistrations
  * getRootSubnetHistory
  * getRootSubnet
  * getHistory
  * getLatest
* client.live - Real-time blockchain data and live network information
  * getFreeTaoBalance
  * getLatestBlockExtrinsics
  * getExtrinsicsForBlockRange
  * getExtrinsicsForSpecificBlock
  * getRawExtrinsicsForSpecificBlock
  * getNodeTransactionPool
  * getNodeVersion
  * getPalletByConstants
  * getPalletEvents
* client.evm - EVM-related operations and data
  * getEVMTransactions
  * getEVMBlocks
  * getEVMContracts
  * getEVMLogs