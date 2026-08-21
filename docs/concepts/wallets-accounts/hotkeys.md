---
title: Hotkeys
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

Hotkeys are part of your Bittensor wallet, and are used to perform actions on the chain in a secure fashion.  [Coldkeys](/docs/coldkeys) can have multiple hotkeys.  Each hotkey can be used to:

* Register a miner or validator on a subnet. (You can use the same hotkey on multiple subnets, but you cannot reuse the same hotkey on a single subnet).
* Stake alpha to a validator's hotkey. Under dTao, tao is converted to the destination subnet's alpha at stake time, and alpha is what is actually staked to the hotkey.

In both of these cases, staking rewards are paid in alpha and credited to the hotkey you staked to.

All stake attached to a hotkey remains under **your** coldkey and can be unstaked back to the coldkey.
