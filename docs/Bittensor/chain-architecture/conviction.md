---
title: Conviction
excerpt: >-
  Conviction is a new (May 2026) feature allowing locking alpha to a subnet to
  show conviction (reduces rugpulls)
deprecated: false
hidden: false
metadata:
  robots: index
---
Conviction has arrived on testnet with a planned mainnet launch of May 13. In this post, we will walk through what conviction is, how it works, and why you should care.

# TL;dr

* Conviction grows from locked alpha
* Conviction growth rate has a half-life of 62 days.
* 100% of SN owner emission is locked.
* Conviction is different from staking.  You still stake and have APY. There is no additional reward from conviction.
* Unlock - immediately drops conviction - alpha is not immediately available for selling
* Available alpha increases over time - 50% after 21 days.
* Locked stake can be transferred (some restrictions apply.)
* Coldkeys can only have conviction to _ONE_ hotkey per subnet.

# What is Subnet Conviction

Buying an alpha token shows support for a subnet.  But does it show conviction?  That you have long term support for the mission of what the team is trying to achieve?  Not really.

Conviction is the lock of your alpha token to the subnet owner’s hotkey. If you _really believe_ in the mission of the SN, you are willing to lock your token to show your conviction.  Once locked - a conviction score will begin to accumulate (with a half life of 62 days.)

<Callout icon="📘" theme="info">
  NOTE:  adding a conviction lock DOES NOT change staking.  It does not affect your yield.  Conviction is a completely different mechanism from staking.

  There is no **additional** yield from conviction.
</Callout>

The hotkey with the most conviction is the “Subnet King.”  Currently, this means nothing, but discussions lead us to believe that the Subnet King will take ownership of the subnet.  So Subnet owners must have high conviction to prevent that from happening.

## Subnet Owner Conviction

Subnet owners (should) have conviction in their subnet.  To enforce a base conviction for subnet owners, all emission to the subnet owner (18% owner share) is automatically locked into conviction on the owner hotkey. With 1296 alpha/day entering conviction to the subnet owner Hotkey, conviction for the subnet owner build quickly.

## Other User’s Conviction

Other users may lock alpha into conviction. If they support the owner - to the owner’s hotkey.  Or they may lock to a different hotkey.

It is assumed (but not yet in the code) that the hotkey that is “Subnet King” will take over owner emissions of the subnet/become the owner.

One coldkey can have conviction to only one hotkey in the subnet.  The staking hotkey can be different than the conviction hotkey.

## Lock to conviction

Once alpha is locked into conviction, it does not immediately become conviction.  The conviction score begins to grow as follows:

![](https://files.readme.io/81cc240700af9e7b379a0fb36082d8635ba0e1480b263168879d765cf0eb68a4-image.png)

<br />

648,000 is 90 days (at 7200 blocks per day).

The half life for conviction is ~62 days.  (if you lock 10,000 alpha, your conviction will be 5,000 in 62 days, 7,500 in 124 days, etc.)

This table shows the conviction over time -showing the increase every 62 days over a year:

![](https://files.readme.io/04d134940f3561998a0d4bf56bc0223f2eb6cb49cad801a33d0441908f53a88a-image.png)

<br />

Every time a new conviction lock/unlock is made, the conviction must be recalculated.  For subnet owners, this will happen every time alpha emission is awarded. And since the conviction for each reward amortizes into conviction differently, each award must be added to the calculation.

So, the formula for subnet owner conviction has:

* Term 1: any initial lock made by the owner
* Term 2: an integral, calculating the conviction for each 0.18 injected each block from start time to block n

![](https://files.readme.io/0a3c27bf9178293075b3b98826b91c3a29d91826dc36ac516dcc56532df8e9c9-image.png)

<br />

This can be simplified to:

![](https://files.readme.io/53c9588e888d94adf53e475c1895cb01ad005f8190936945796c80e8be3f0608-image.png)

<br />

Over a year, this looks like (difference is the b0 initial lock):

![](https://files.readme.io/812fff3b48fcc67484781133c5a922612e9852b197d9e7cd208cdbb2cc42e8dd-image.png)

<br />

This assumes that all locked alpha remains locked in conviction.

# Unlocking Alpha from conviction

If you lose conviction in a subnet (or if you are a subnet owner, and you need to pay expenses), you can unlock your alpha.

When you unlock alpha:

* Conviction IMMEDIATELY drops by the amount unlocked.  For example:i f your conviction was 100,000, and you unlock 50,000, your conviction becomes 50,000.
* Unlocked alpha is not immediately available.  It becomes available at a decay rate with a half life of 20.8 days.

![](https://files.readme.io/73aabaef796cbc3ef2a960b5a2b9c15bf1eea4950f09ec702201f13ea5b21388-image.png)

![](https://files.readme.io/3bb29382c3665638db7b17d3d459b11e9c0187e8c15c7fd3dc81ba3ccb04b5bf-image.png)

<br />

This means that subnet owners (who receive most of their alpha in emissions) will be unable to rugpull their alpha - any unlock comes with ~3 months delay to extract 95% of the value.

# Conviction Scoring after an unlock

When an unlock occurs, the conviction equation must be rebased to the unlock event.

![](https://files.readme.io/e72d34ba54c2b446c8c5cbbb04bb85b5fdc7098e328c72c915d12f184bd4e56c-image.png)

For every block after this unlock of 75, there is an initial conviction of 25. (The conviction drops by the amount unlocked.)

The conviction is updated from the instantaneous conviction at time/block f by subtracting the unlock.

![](https://files.readme.io/f4acb93c89a68c0504e8a4a7dd1b3e1f8223e6fc0fce9f146b3aaf1bac2d8552-image.png)

<br />

The new basis for conviction is b1, which is b0 - u.  Extending out for multiple unlocks (k unlocks):

![](https://files.readme.io/5118db9852787ab1141463a59f00df0cf103ebae983b472c38b0ed3d9c182d54-image.png)

<br />

The new conviction formula has 3 terms: Conviction at the last unlock Growth of existing alpha (bk - Cfk) Owner emission that grows every block after block fk

![](https://files.readme.io/906141d0b743f85cfe05eb72ae8eba2a942a1266577bb0ad00d702ca683fadf6-image.png)

<br />

# Modeling an attack for Subnet King

Using the above formula, we can model the subnet owner’s Conviction, and the conviction of an attacker, and understand if the attacker will succeed in current circumstances, or if the attack will fail.  The Subnet owner could add more alpha, and model how “well” it does to prevent the attack:

![](https://files.readme.io/7e1a77cd51f61ac0dbeb524b83f67e4a823dbdc9f5c7b5d7b93058c40ae06055-image.png)

<br />

# Transferring locked alpha

There are rules to transferring locked alpha.  If an alpha transfer occurs inside a subnet, locked alpha is used, only after all other options have been exhausted:

<br />

1. Free alpha (alpha that is not in the conviction mechanism) is utilized first.
2. Available alpha is the next store to be depleted.
3. Unlocked alpha.

If all of the free/unlocked/available alpha has been depleted, the locked alpha will be transferred.  
Conviction is also transferred proportionally.  If there is 10,000 locked, and the conviction is 5,000, 50% of the locked alpha has conviction.  So 50% of the transferred locked alpha will also have conviction.

if the coldkey receiving the transfer has a conviction with another hotkey - the transaction will fail.  Each coldkey can only have conviction with one hotkey.

# Jupyter Notebook

The charts and code in this example can be found on GitHub

https://github.com/taostat/awesome-taostats-api-examples/blob/main/python/conviction_maths.ipynb
