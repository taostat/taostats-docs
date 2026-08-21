---
title: Using Taostats Tax Reporting
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

Taostats can help you prepare your income statements

No matter if you are a subnet owner, miner, validator, or you stake in Bittensor, eventually it will become time to report your actions on your taxes.

Bittensor is truly a global economy, and Taostats does not employ tax professionals, nor are we experts at global tax law.  But, we do have the data that can help you (or your tax professional) prepare your taxes.

At [https://taostats.io/pro/tax](https://taostats.io/pro/tax) , you can find tooling that provides you with annual returns for every token you have purchased in the Bittensor Network:

<Image border={false} alt="Taostats Pro tax report form with coldkey address, start and end date fields for 2025, and an open token dropdown listing TAO and subnet tokens" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/401d5f19d56f744b.png" />

This reporting does require a paid Taostats plan.

For each subnet, you will receive a CSV.

Our reports are based on the following:

* the time zone is UTC - matching the blockchain time
* the daily income is attributed to the wallet on the last block of the day
* The subnet price is read from the chain on the last block of the day
* The USD/TAO uses the closing price from CMC (Coin market cap uses UTC)
* All transactions use the subnet price and CMC price at the time of the transaction (block)
* The subnet income reported is the sum from all sources (staking, owner, validating, mining)

# Possible tax transactions:

**Here are the ones you will probably care about**
"transfer\_out"
"token\_swap"
"transfer\_in"
"transaction\_type"
"fee"

**But these also exist:**
"liquidity\_fees\_claimed"
"liquidity\_added"
"coldkey\_swap"
"dust\_lost"
"tip"
"burned\_register"
"liquidity\_removed"
"subnet\_registration\_cost"
