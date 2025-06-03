---
title: Parent Hotkey Validation
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
In September 2024, the Bittensor chain launched parent hotkeys - a way for validators to earn tao from stake, without actually running a validator on the chain.

## Parent hotkeys

A parent hotkey allows a validator to add their stake to an existing validator.  This increases the total stake for that validator on the subnet.\
In the Subnet metagraph, and yellow stake value indicates parent hotkeys. Clicking the carat opens a view to show all of the parents (and the percentage of their stake) added to the child hotkey.

![](https://files.readme.io/d882bdb6639df5e533b69699ccde202c85727b5d188ba3dc50adf924b7a460b8-image.png)

<br />

For the benefit of being a parent hotkey, taostats charges a child take of 4.5% - so the returns of PRValidator and Love are reduced by 4.5%,  and the 4.5% is distributed to taostats and their stakeholders.

## Why Parent hotkey?

* A parent hotkey does not need to run a neuron.
* Can begin building a validator while validating (many subnets have minimum stake requirements.)

<br />

## Can parent hotkeys “beat” existing validator returns?

Based on our research, if the parent hotkey chooses child validators with high Vtrust, the parent hotkey can have competitive returns, but they will never have higher returns than the validator they are parenting on.