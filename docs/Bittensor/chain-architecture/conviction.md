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
Conviction has arrived on testnet. There was a full page here, but then V2 was submitted, and it is under active development.

As of May 15 at 1100 EDT, this is the current status of conviction:

*  Conviction is different from staking.  You still stake and have APY. 

## Lock 

* Conviction grows from locked alpha. 
* PerpetualLock on: locked alpha remains locked. (default) 
* PerpetualLock off: locked alpha decays to an unlocked state. 
* Lock decay has a half life of 110 days. 
* Locked stake can be transferred (some restrictions apply) 
* 100% of SN owner emission is locked. 

## Conviction growth 

* Conviction growth rate has a half life of 132 days. (if you have perpetual lock off - the math gets gnarly.) 
* All Owner locks converts to 100% conviction immediately - no formula 
* There is no _additional_ reward from conviction.

## Subnet King 

* The hotkey with the highest conviction can take subnet ownership 
* Subnet > 1 year old.  Conviction > 10% of alpha_in. Different coldkey from current owner.
