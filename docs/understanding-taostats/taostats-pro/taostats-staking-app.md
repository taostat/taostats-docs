---
title: Simple
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

The taostats staking app gives a number of ways to stake tao and alpha

The [Taostats Staking App](https://taostats.io/pro/stake) is part of the taostats dashboard. There are a few options to stake here:

* ## [Simple](#simple-1)
* ## [Manual](#manual-1)
* ## [Balance](#balance-1)
* ## [Automate](/docs/#automate)

> 📘 **[Connect your wallet](/docs/connecting-your-wallet) to ensure you can stake**

Simple staking makes it easy to perform one or two stake transactions at a time.  You can buy/sell existing stake positions, or add a new one.

### Existing positions

<Image border={false} alt="Taostats simple staking existing positions list with rows showing subnet, validator, alpha and TAO balances, and buy and sell buttons" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/271c37e26b7cdf79.png" />

Click the Buy or Sell to begin a transaction

### New positions

<Image border={false} alt="Taostats staking add-transactions bar showing total and available balances with buy, sell, and reset buttons to start a new position" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/e2c23b5beba743d5.png" />

Complete your buy or sell by filling in the details in the box

<Image border={false} alt="Taostats new position buy form with subnet and validator dropdowns, a manual hotkey option, amount inputs, slippage, Max button, and available balance" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/724076c899aa494d.png" />

When you are finished - click Next, confirm the transactions, and enter your password.  Your wallet app will complete the transaction.

&#x20;

<Image border={false} alt="Taostats new position action panel with buy, sell, and reset buttons and a next button to calculate fees and proceed" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/36427bb5c645ce3a.png" />

# Manual

The Manual staking page lists all of your current stakes, with sliders.

<Image border={false} alt="Taostats manual staking list with per-stake rows showing subnet name, an adjustable slider, slippage indicator, amount pill, and percentage" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/a7d59b404c1716bc.png" />

Unlike the balance page, these sliders run independently, and lowering the stake of one subnet does not increase the value of the others.

# Balance

> 📘 **Undelegating & Unstaking - negative stake is removing stake from that validator.**

<Image border={false} alt="Taostats staking app balance overview with my TAO balance, an allocation slider with percentage, and available-to-delegate amount above a subnet list" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/41bb3c9b547b02cd.png" />

## Tao overview

Select how much tao you have set available to delegate. In this screenshot 27.47 tao is delegated of 31.13 total tao (88.58%)

<Image border={false} alt="Taostats TAO overview slider showing total TAO balance, an allocation percentage, and the amount available to delegate with USD equivalents" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/db623e1082d79fd0.png" />

Moving the slider to the left will reduce the amount of tao being staked. Moving to the right will add more tao to be staked.

## Slippage

<Image border={false} alt="Taostats per-stake slider row with a Max Slippage tolerance field and info icon controlling the amount of TAO staked" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/d371671002a9158c.png" />

Set the Max Slippage you are comfortable with having on any Stake event.

## Stakes

<Image border={false} alt="Taostats manual staking list of stake rows, each with an allocation slider, slippage readout, lock icon, value pill, and remove control" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/a5eb3656001ca32c.png" />

This screenshot is from testnet, so the validator name is "Unknown."

Moving the sliders will change the staking for all subnets.  The Lock prevents a stake from changing.

### Example

In the screenshot the amount of stake from SN1 drops from 25 tao to 12 tao. The other subnet's stake grows proportionally. Note that SN19 has 1.55% slippage, which is over the Max Slippage value, and appears in red.

<Image border={false} alt="Taostats manual staking sliders showing stake rebalancing across subnets with color-coded slippage warnings, one highlighted over the max in red" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/0e6b0f7803fd632f.png" />

## Fees

Every staking and unstaking action on the chain costs has a fee. This fee is different on each subnet [Get Subnets](/api/) has this parameter.

<Image border={false} alt="Taostats delegation summary modal showing a single delegation with slippage and a separated estimated fee box" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/0b726bb77c7ec77e.png" />

### Multiple transactions

If there are multiple actions - this fee is assessed for each action.

All of the actions are run inside a batch command, which is also assessed a fee on chain:

<Image border={false} alt="Taostats delegation summary modal listing multiple batched delegations with per-row slippage and a single consolidated estimated fee" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/d2d0ec6e7121d241.png" />

Once the change has been made, the final fee can be seen in the Extrinsic:

<Image border={false} alt="Taostats extrinsic detail showing a Utility.batch_all name and the total extrinsic fee in TAO with a USD equivalent" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/fe85e834ea28b005.png" />

> 📘 **These are chain fees. Taostats does not charge for staking or unstaking.**

# [Stake troubleshooting](/docs/stake-troubleshooting)
