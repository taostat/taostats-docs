---
title: URL Format
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

The Single Account page gives you details about a wallet address

The general format for the URL is `https://taostats.io/account/<wallet>` address.  See an [example wallet](https://taostats.io/account/5CcH9xVPJY2Nc9Wovft6Lr2qoQzefEEJfqgVhSrXdAx2ixGr).

# Summary

The top of the page has a wallet summary:

<Image border={false} alt="Taostats account summary panel with balance, delegated breakdown, 24-hour change, and creation date cards plus block, address, and public key metadata" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/3732672b75143c2c.png" />

* **Balance**: Both in tao and USD.  The arrow indicates the % change in the last 24 hours.
* **Delegated**: Bar chart breaking down the distribution of tao.
  * Staked to root
  * Staked in alpha
  * Free tao
  * [Liquidity](/api/) Positions: amount in liqudity positions
  * Reserved: Tao placed in reserve (generally when a proxy is added)
* **24h balance change**: In tao and USD.
* **Wallet Creation Date**: Date the wallet was created
* **Address**: coldkey and public key

# Alpha Balances

This table shows all alpha stakes with initial sort on % of stake

<Image border={false} alt="Taostats account Alpha Balances table with columns for subnet, validator, percent of stake, alpha balance, and TAO-equivalent balance, plus a currency toggle and pagination" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/e44d8842dab3b882.png" />

* **Subnet**: The subnet with stake
* **Validator**: Validator that is staked to
* **Chart**: Dropdown opens a chart (see [Alpha chart](#alpha-chart) )
* **% of stake**: Percentage of stake (converted to tao)
* **Balance**: Alpha balance
* **Balance Tao**: Alpha balance converted to tao.
* **Data**

## Alpha chart

For each stake held, there is a chart with a carat.  Clicking opens a drawer in the table.

<Image border={false} alt="Taostats account alpha stake row expanded to a drawer showing 24-hour change cards and a dual-axis line chart of alpha and TAO balance over time" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/2ed0835059e5d4a5.png" />

* 24 hour change in alpha and tao
* Chart of historical stake - showing both value in tao (red) and value in alpha (teal)

# Alpha Staking Transactions

<Image border={false} alt="Taostats account Transactions table with subnet, amount, and type filters and columns for time, action, subnet, delegate, alpha, tao, and tao price" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/05977a17c082014b.png" />

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

<Image border={false} alt="Taostats account Transfers table listing TAO transfers with columns for direction, extrinsic, from, to, amount, and time, plus filters and CSV export" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/d5cbfac34733deaa.png" />

* **Arrow**: Green indicates "tao coming in", red indicates "tao going out"
* **Extrinsic**: the chain extrinsic for the transaction. Clicking opens the extrinsic
* **From**: Coldkey sending tao
* **To**: Coldkey receiving tao
* **Amount**: tao sent
* **Time**: When the transaction occurred. Mouseover for GMT date/time

# Extrinsics

This table lists the account's on-chain extrinsics — the signed calls this coldkey has submitted.

* **Extrinsic**: the extrinsic ID; clicking opens its [detail page](/docs/extrinsics-detail).
* **Block**: the block the extrinsic was included in.
* **Call**: the pallet and method called (e.g. `Balances.transfer`, `SubtensorModule.add_stake`).
* **Time**: when it was submitted (mouseover for exact GMT).

# Proxies

The Proxies tab lists every [proxy](/docs/securing-a-wallet) set on the account, and the type of each.

* **Delegate**: the account authorised to act on this coldkey's behalf.
* **Type**: the proxy type, which scopes what the delegate may do (e.g. `Any`, `Staking`, `Transfer`, `Governance`).
* **Delay**: the announcement delay (in blocks) before a proxied call can execute, if set.

# Claims

The Claims tab lists the account's most recent **root claims** — the manual `claim_root` calls that realise root staking rewards under [Root Reborn](/docs/root-validator-baskets).

* **Time**: when the claim was made.
* **Amount**: the TAO realised by the claim.
* **Extrinsic**: link to the `claim_root` extrinsic.

# Conviction

The Conviction tab shows the [conviction](/docs/conviction-v2) this account has placed, per subnet.

* **Subnet**: the subnet the conviction is locked on.
* **Conviction**: the current conviction weight.
* **Locked**: the alpha locked and, where applicable, the unlock schedule.
