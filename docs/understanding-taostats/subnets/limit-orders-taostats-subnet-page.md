---
title: Limit Order Setup
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

Place limit orders to buy/sell alpha

On the subnet landing page, below the trading view chart is the staking interface:

<Image border={false} alt="Taostats subnet page trading view candlestick chart above a staking panel with connected-wallet controls and stacked buy and sell cards" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/659823606adad095.png" />

To access the Limit Order interface, select the `Limit` option in the upper right corner of the Staking menu.

You must provide Taostats with access to buy and sell subnet tokens on your behalf.  Since your limit order may hit its threshold at 3 AM while you are asleep.

<Image border={false} alt="Taostats limit order setup panel prompting the user to grant proxy access to trade subnet tokens, with a reassurance notice and a grant-access button" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/5282a5b04c74fb8e.png" />

## Granting access

Note that granting access has a fee that is locked on chain while taostats has proxy access:

<Image border={false} alt="Taostats grant access confirmation dialog explaining the proxy approval, wallet fund safety, and how to revoke, with a note about the refundable on-chain locked fee" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/3f1c028397e6c0af.png" />

# Limit Orders

The limit Order UI is very similar to the buy/sell menu.  Choose:

<Image border={false} alt="Taostats limit order interface with mirrored buy and sell panels offering validator, price, alpha/tao amount, and MEV tolerance fields plus fee and slippage estimates" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/98aae528d2468e84.png" />

* Validator
* Buy or sell price
* Amount of tao/alpha to buy/sell
* MEV Tolerance: [Slippage](/docs/slippage)

Add in your values

## Fee

<Image border={false} alt="Taostats limit order form showing price, paired alpha and tao amount fields, MEV tolerance, and estimated alpha, fee, and slippage with an insufficient-funds warning" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/45639a7dc757e938.png" />

Once you insert your limit order, you will see an estimated fee. This is a fee to pay taostats to handle chain fees and running the proxy.

Add your balance for all limit order fees.  This will be paid to taostats to handle all your future limit orders.

<Image border={false} alt="Taostats top up balance dialog for limit order fees showing token and USD balance, preset and custom amount buttons, and a top-up action button" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/3e21e3a97fcc52e7.png" />

Taostats tracks the fees you have paid and how much fee balance you have left.

<Image border={false} alt="Taostats fee balance indicator showing the remaining limit order fee balance in USD and TAO side by side" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/0bde108e9883e58a.png" />

Once you set the order, your order will appear in the tables below:

* Order Book
* Pending Orders
* My Completed Orders
* My Failed Orders.

There is a button to `Remove Taostats Access` to cancel and stop all Limit orders.  Taostats will no longer have proxy access.
