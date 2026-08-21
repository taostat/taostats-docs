---
title: Staking on the Subnet Page
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

You can now stake right on the Subnet page

On each subnet page, there is the ability [to connect your wallet](/docs/connecting-your-wallet) and stake to the subnet.

<Image border={false} alt="Taostats subnet staking panel with mirrored buy and sell cards showing token amount inputs, slippage, Max buttons, balances, and action buttons" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/c8307579c8e1194f.png" />

In the screenshot above:

* there is 3.66 tao that can be used to buy alpha.
* There is 0.149 alpha that can be sold for tao

## Max

clicking the Max button will use all of your available tao/alpha to buy/sell. The slippage number will update with the estimated slippage for the transaction.

<Image border={false} alt="Taostats buy panel showing token amount inputs, a slippage indicator, a Max button, and available balance for staking" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/751c5b33deaef30b.png" />

## Buy/Sell

On clicking the buy or sell button, a popup will appear:

<Image border={false} alt="Taostats buy confirmation popup summarizing the token amount, cost in TAO, routing providers, and slippage with a confirm button" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/f02dd64e779268ff.png" />

Clicking confirm will open a dialog from your wallet application confirming the sale:

## Settings

Adjust your validator of choice, and the amount of slippage that is acceptable

<Image border={false} alt="Taostats staking settings modal with a validator selection dropdown and a max slippage input field plus a done button" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/23108e8d35302485.png" />

## Fees

There are staking and unstaking fees on Bittensor.

* Root subnet: no staking or unstaking fees
* Fee is a percentage (that can be adjusted by the subnet owner.
  * Fee is taken as tao when staking
  * Fee is taken as alpha when unstaking

If you utilize multiple staking actions using taostats, they will be sent to the chain in a `batch`.  Batch calls on chain have a small fee.  Taostats does not collect this fee, it is paid to the chain.
