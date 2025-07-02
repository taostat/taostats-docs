---
title: 'Limit Orders: Taostats Subnet Page'
excerpt: Place limit orders to buy/sell alpha
deprecated: false
hidden: true
metadata:
  robots: index
---
On the subnet landing page, below the trading view chart is the staking interface:

<Image align="center" width="50% " src="https://files.readme.io/f78386bce564e0f47101d282f08e4e2ed199a544c34a8a8941004af2614a5d84-image.png" />

# Limit Order Setup

To access the Limit Order interface, select the `Limit` option in the upper right corner of the Staking menu.

You must provide Taostats with access to buy and sell subnet tokens on your behalf.  Since your limit order may hit its threshold at 3 AM while you are asleep.

![](https://files.readme.io/dc1e10c5e9a988cfc2424ff0577809e49e19e188d09b61a1168bd599a0ffeea8-image.png)

## Granting access

Note that granting access has a fee that is locked on chain while taostats has proxy access:

<Image align="center" width="75% " src="https://files.readme.io/7988bb03b165ed881c020319a693f60972d5a662e77512c0fcf0beef73b466fd-image.png" />

<br />

# LImit Orders

The limit Order UI is very similar to the buy/sell menu.  Choose:

![](https://files.readme.io/45c86c9de129dca331bee5e8e3b39f695a7e7d82b0559f325fb244e33d9e10e6-image.png)

* Validator
* Buy or sell price
* Amount of tao/alpha to buy/sell
* MEV Tolerance: [Slippage](doc:slippage)

Add in your values

## Fee

![](https://files.readme.io/ba9229f7165f1303e648497f430513c0e8965420fc0c38f3a8adee8e2df00757-image.png)

Once you insert your limit order, you will see an estimated fee. This is a fee to pay taostats to hndle chain fees and running the proxy.

Add your balance for all limit order fees.  This will be paid to taostats to handle all your future limit orders.

![](https://files.readme.io/19a5b8a8800ab660dba156f822204dd69227cc90e89ef16acc9cb23f57156c47-image.png)

Taostats tracks the fees you have paid and how much fee balance you have left.

![](https://files.readme.io/51d08a90a405a971fdac89207f7437d4b86f0e0656ee5ab534bfb82f4b8a10ae-image.png)

<br />

Once you set the order, your order will appear in the tables below:

* Order Book
* Pending Orders
* My Completed Orders
* My Failed Orders.

There is a button to `Remove Taostats Access` to cancel and stop all Limit orders.  Taostats will no longer have proxy access.