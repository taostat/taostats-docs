---
title: Single Account Page
excerpt: The Single Account page gives you details about a wallet address
deprecated: false
hidden: false
metadata:
  robots: index
---
# URL Format

The general format for the URL is \[https\://taostats.io/account/\<wallet]\(https\://taostats.io/account/\<wallet) address.  \[example wallet]\(https\://taostats.io/account/5CcH9xVPJY2Nc9Wovft6Lr2qoQzefEEJfqgVhSrXdAx2ixGr)

# Summary

The top of the page has a wallet summary:

![](https://files.readme.io/ae2ec87ec00c6e9fad81a4e877ccce1f5fa960aa7070bcdef6f4825fca2be964-image.png)

<br />

* **Balance**: Both in tao and USD.  The arrow indicates the % change in the last 24 hours.
* **Delegated**: Bar chart breaking down the distribution of tao.
  * Staked to root
  * Staked in alpha
  * Free tao
  * [Liquidity](ref:liquidity) Positions: amount in liqudity positions
  * Reserved: Tao placed in reserve (generally when a proxy is added)
* **24h balance change**: In tao and USD.
* **Wallet Creation Date**: Date the wallet was created
* **Address**: coldkey and public key

# Alpha Balances

This table shows all alpha stakes with initial sort on % of stake

![](https://files.readme.io/6e39332b1ee10d9e73d4b65217205a70765629c3705d609d1b2f79071e7b990f-image.png)

* **Subnet**: The subnet with stake
* \*\* Validator\*\*: Validator that is staked to
* **Chart**: Dropdown opens a chart (see [Alpha chart](#alpha-chart) )
* **% of stake**: Percentage of stake (converted to tao)
* **Balance**: Alpha balance
* **Balance Tao**: Alpha balance converted to tao.
* **Data**

## Alpha chart

For each stake held, there is a chart with a carat.  Clicking opens a drawer in the table.

![](https://files.readme.io/478b2cc5a0805a8768d71720592ff05907d78eda18e2e82dde3630cbe5eb9bce-image.png)

* 24 hour change in alpha and tao
* Chart of historical stake - showing both value in tao (red) and value in alpha (teal)

# Alpha Staking Transactions

![](https://files.readme.io/f86d56ccbcc4ee2582a72b87059de5b501d87356564cbe84c873712a79f6ebc8-image.png)

This table can be sorted by Subnet, Type, and Amount

* **Time**: when the transaction took place (mouseover for exact time in GMT)
* **Action**: Buy, Sell, Transfer In, Transfer Out.
  * Buy and sell are transfers of tao and alpha
  * Transfer in/out are changes in validator or Subnet of alpha.
* **Subnet**: The alpha purchased/sold
* **Delegate**: The validator staked to.
* **Alpha**: The amount in alpha
* **Tao**: the amount in tao.
* **Tao Price** the price of the alpha (in Tao) at the time of transaction.
* **TXN** a link to the Extrinsic of the transaction.

# Transfers: Tao Transactions

This table lists all transactions of tao in and out of the wallet

![](https://files.readme.io/677f8f9648417dc45691f5cb0258fb303c2c22ed1860d7491905b7a95856af83-image.png)

* **Arrow**: Green indicates "tao coming in", red indicates "tao going out"
* **Extrinsic**: the chain extrinsic for the transaction. Clicking opens the extrinsic
* **From**: Coldkey sending tao
* **To**: Coldkey receiving tao
* **Amount**: tao sent
* **Time**: When the transaction occurred. Mouseover for GMT date/time

<br />

# Extrinsics