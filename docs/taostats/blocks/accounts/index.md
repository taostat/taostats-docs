---
title: Accounts
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
**[Blockchain -> Accounts](https://x.taostats.io/#accounts)** lands at the blockchain page, and highlights the Accounts table. This table lists all of the accounts on the Bittensor blockchain and is initially sorted by the total tao associated with the coldkey.

![](https://files.readme.io/2106671-image.png)

* **Account**: coldkey for the wallet.
* **Free**: tao that is not delegated
* **Delegated**: tao that is delegated.
* **Total**: A sum of free and delegated.

> 📘 Note: tao that is staked to a hotkey is *not* displayed. This is a known issue, and will be resolved.

* **Last Update**: The last block where a change was made.

# Account details

Click on any hotkey to go to the Account details page.

## Overview

The top of each account page details the Account's addresses, hotkey, public key, and when it was created.

We can also see the current breakdown of Delegation (in the screenshot below, staking is split amongst 4 validators). Tao delegated to a hotkey is not shown.

![](https://files.readme.io/84f608f-image.png)

## Balance chart

![](https://files.readme.io/cba2154-image.png)

A breakdown of Free/delegated/total TAO over time. 

> 📘 In the chart above, we can see where TAO was unstaked, and then restaked.
>
> In December, a large if TAO was added and immediately staked.

## Delegation Chart

![](https://files.readme.io/6c6e0c5-image.png)

In the above chart, we can see how the delegation for this user has changed over time.  All hotkeys and delegation appear on this chart.

## Extrinsics Chart

![](https://files.readme.io/f29f6ee-image.png)

A breakdown of the Extrinsics associated with this hotkey.

## Transfers

![](https://files.readme.io/7a88014-image.png)

Extrinsics that are ***only transfers***. It is possible to click on the other party's hotkey to explore that user.

## Delegation

![](https://files.readme.io/95c1fa0-image.png)

Extrinsics that are only Delegation/undelegation events.
