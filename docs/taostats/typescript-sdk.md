---
title: TypeScript SDK
excerpt: >-
  Are you a TypeScript developer using our APIs?  Our SDK might slimplify
  things!
deprecated: false
hidden: true
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