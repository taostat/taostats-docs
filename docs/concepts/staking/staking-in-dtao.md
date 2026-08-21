---
title: Staking Options
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

Staking tao/alpha is how investors earn yield.

> 📘 Staking with taostats
>
>   See [Staking Instructions](/docs/staking-instructions) for a number of pages describing how to stake using Taostats.

Staking plays a principal role in the functioning of the Bittensor network. In February 2025, the dTao release gave stakeholders additional power: staking into a subnet increases the emissions of the subnet.

in dTao, there are two options for staking:

* [Staking to root](#staking-to-root)
* [Staking to a Subnet](#staking-to-alpha)

# Staking to root

Staking to root uses only tao. Your tao is staked on a root validator, and you receive returns based on the validator's performance in the subnets.

Staking to root is a `safe` staking option — there is no way to lose tao value. However, root staking decreases over time [by design](/docs/stakeholder-emissions-root-vs-alpha), as the root proportion decreases on all subnets.

## Root rewards under Root Reborn

Root dividends are handled by **[Root Reborn](/docs/shorting-explainer)**, live on mainnet (subtensor `spec_version` 441). It replaced the earlier auto-compounding and "keep vs. swap" claim options — there is **no auto-claim**.

Instead, each root validator curates a **basket**: your root dividends are auto-sold to TAO (as before) and immediately re-bought across a set of subnets the validator chooses, then held as compounding subnet-alpha exposure until you redeem. You pick a validator on its basket, not just its take rate — a validator that publishes no basket buys nothing, and its stakers earn no root reward that cycle.

Your balance no longer rises on its own. To realise rewards you make a single manual **`claim_root`** call, which sweeps every validator you have root stake with, values your basket shares at current NAV, and swaps them **to TAO** (there is no "keep as subnet alpha" redemption). Claiming costs a fee that scales with basket width, so prefer a concentrated basket and claim infrequently — and **claim before switching or unstaking** from a validator, or your claim on that basket drops toward zero.

For the full mechanics — the basket vector, how shares accrue, fees, and per-participant impact — see **[Root Validator Baskets](/docs/root-validator-baskets)** (the short canonical reference) and the [Root Reborn explainer](/docs/shorting-explainer) and [TL;DR](/docs/tldr).

Root dividends accrue to your basket roughly every 2 days (the chain awards them somewhat randomly — a week between accruals is not abnormal), but they only reach your balance when you make the manual `claim_root` call.

# Staking to alpha

This is the new feature and primary goal of dTao - to enable stakeholders to vote and determine the emissions for every subnet.

To stake in alpha, tao is exchanged via the [Subnet Pools](/docs/subnet-pools) into alpha.  This will incur [Slippage](/docs/slippage). The received alpha is then staked to the validator selected.  Your returns will be in alpha, and autocompounded to the validator hotkey.

Because alpha staking trades through a subnet pool, it can be front-run by MEV bots that worsen your slippage. Taostats protects alpha stake/unstake transactions with [MEV Shield](/docs/mev-shield), which encrypts the transaction so bots cannot read or front-run it.

Staking to alpha *does* incur risk: a drop in alpha token price will result in a lower amount of tao when unstaking.

Emission is awarded every 360 blocks (approx 72 minutes).

> 📘 **No unbonding period**
>
> Unstaking is immediate — there is no lock-up or unbonding delay. As soon as an unstake settles, the resulting tao is in your free balance and spendable right away. (The exception is [conviction locks](/docs/conviction-v2): alpha locked in conviction **cannot be unstaked** while the lock is active — your total staked alpha on the subnet must stay at or above the locked amount. Only alpha held *above* the locked amount is unstakable.)

## Staking fees

For all staking transactions there is a small extrinsic (transaction) fee charged by the chain. Taostats currently does not allow staking every last tao — it leaves a small amount behind to cover the fee for the eventual unstake transaction.

### Root

There is no **additional** staking fee to stake or unstake from root — only the standard chain extrinsic fee applies.

### Subnets

* Staking and unstaking through a subnet pool carries a fee that defaults to **0.05%** of the stake/unstake value.
* This can be changed by the subnet owner, so read the current value before you stake.

### Get the current fee (and price) for a subnet

The live pool endpoint [`GET /api/dtao/pool/latest/v1`](/api-reference/subnet/get-pool-latest/) returns the subnet's current **`fee_rate`** (staking/unstaking fee) along with its **`price`** in TAO. Pass the `netuid` for the subnet you want.

## Moving stake

The move stake command can be used to switch validators in a subnet.  Under the hood, this is an unstake, and then staking.  However, only one fee is charged.

There are three distinct operations for relocating an existing position — they are easy to confuse:

* **Move** (`move_stake`) — re-delegate a position to a different hotkey and/or a different subnet. You keep ownership. Moving across subnets swaps through both pools and incurs slippage on each leg.
* **Swap** (`swap_stake`) — move a position to a *different subnet* on the *same* hotkey. Both legs (sell on the origin pool, buy on the destination pool) can incur slippage, and the two subnets must differ.
* **Transfer** (`transfer_stake`) — hand the position to **another coldkey**. After this, that coldkey controls and can unstake the funds — not you. This is a transfer of value and is **irreversible**; double-check the destination address.

## Unstaking everything at once

The "unstake all" operations sweep your entire stake on a hotkey in one call, but they behave differently from a normal unstake and have two things worth knowing:

* **No slippage protection.** Each pool swap executes at the current price with no limit, so large positions can incur significant slippage.
* **Silent skips.** Subnets where subtoken trading is disabled, or where a position is dust below the chain minimum, are silently skipped — the call can *succeed* while leaving some stake untouched.

`unstake_all` returns everything to your free tao balance; `unstake_all_alpha` sells your alpha positions and restakes the proceeds as tao on root (netuid 0), keeping the funds staked.

## Root or subnet — which should I stake to?

* **Root** uses only TAO and carries no price risk, but its returns decline over time [by design](/docs/stakeholder-emissions-root-vs-alpha) as subnets take a growing share of emissions. Rewards are realized on a manual `claim_root` (see [Root Validator Baskets](/docs/root-validator-baskets)).
* **Alpha** (subnet) staking buys a subnet's token, which can appreciate or depreciate against TAO — higher potential return, higher risk, and it incurs [price impact](/docs/slippage).
