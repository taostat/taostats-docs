---
title: Changing the timeframe
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

The portfolio page gives you detailed information about a wallet's staking history

When a wallet is selected, data begins to appear:

<Image border={false} alt="Taostats Pro portfolio overview showing wallet balance, earnings, gains, wallet rank, and a dual-line TAO/USD value chart" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/f429401aae1c002f.png" />

The current view is 1 Month - in tao.

The timeframes available are 1D, 1W, 1M and 1Y.  The values can be shown in Tao of USD.

<Image border={false} alt="Taostats Pro portfolio timeframe toggle set to 1M with a TAO/USD currency switch set to TAO" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/9cc44b2a47962d04.png" />

# Balance

Wallet balance in tao and USD

<Image border={false} alt="Taostats Pro portfolio Balance panel showing the wallet's TAO balance, USD value, and 24-hour change" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/f66a3b959138642a.png" />

# Earnings

The values here depend on the timeframe selected.  This screenshow shows a 5% growth, and 64% APY if extrapolated for a year.

<Image border={false} alt="Taostats Pro portfolio Earnings, Gains, and Wallet Rank cards showing TAO earned, APY, and holder rank" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/fbb19aa13d7a5e3a.png" />

# Chart

<Image border={false} alt="Taostats Pro portfolio value chart with a teal TAO line and red USD line over roughly one month, labeled with high and low endpoints" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/987dbdf6160eddc4.png" />

See how your portfolio has changed over time.

Red is USD value, and teal is tao value.

# Holdings

<Image border={false} alt="Taostats Pro portfolio Holdings table listing each subnet position with validator, stake percentage, alpha balance, TAO balance, earnings, and estimated APY" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/d8fc019e9f5e0db4.png" />

The holdings chart shows what alpha you hold.

* Holding: The subnet
* Validator: The validator you are staked to.
* % of Stake: Percentage of your stake on this vali/subnet combo.
* α Balance:  Balance in alpha
* τ Balance: Balance in tao.
* α Earnings:  Earnings in alpha over the selected timeframe
* τ Earnings:  Earnings in tao over the selected timeframe
* % Earnings:  Percentage change over timeframe
* EST APY: Actual Earnings over the timeframe - extrapolated to one year.

> 📘 **Why is the % and APY grayed out?**
>
> If you have purchased or sold alpha in the timeframe - we cannot calculate your actual earnings over that period. Try a shorter period, or wait until it has been a day/week, and your actual earnings will appear.

* Buy: But more of this alpha
* Sell: Sell this alpha
* Data:  Dig deeper

# Transactions

<Image border={false} alt="Taostats Pro portfolio wallet Transactions table of recent subnet buys via Opentensor Foundation with time, type, subnet, alpha, TAO, and price columns" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/dc277f4ec635bb05.png" />

This table is similar to [Staking Transactions](/docs/delegation), but just for your wallet.
