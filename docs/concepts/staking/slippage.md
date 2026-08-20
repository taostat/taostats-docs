---
title: Price Impact and Slippage
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

**Slippage** is the difference between the amount of tao or alpha you *expected* from a trade and the amount you *actually* received. When you stake or unstake through a subnet (liquidity) pool, you almost never get the exact quantity implied by the quoted price — the shortfall is slippage, usually shown as a percentage.

Slippage (the umbrella term) has two components:

- **Price impact** — the inherent, predictable part. It comes down to **how big your transaction is** relative to **how much liquidity is in the pool**. A large trade against a small pool moves the price a lot; a small trade against a deep pool barely moves it. Price impact happens even if you are the only person trading.
- **Slippage (price action)** — the part caused by *other* trades. Between the moment your transaction is submitted and the moment it lands, someone else can stake or unstake in the same pool and move the price, so you receive more or less than you expected. This is often just **another random stake or unstake** happening near yours — it is not necessarily anyone acting against you. In the worst case it *can* be deliberate **front-running** (an [MEV bot](/docs/mev-shield) trading ahead of your transaction on purpose), which Taostats defends against with [MEV Shield](/docs/mev-shield) (see below).

> 📘 **The larger the purchase amount, the higher the price impact**
>
> ### The smaller the liquidity pool, the higher the price impact.

## What is Price Impact?

Due to the limited resources of the liquidity pool, any change in the ratio of tao/alpha will affect the price and exchange rate.  The act of making a purchase through the subnet pool changes the ratio, and affects the rate at which the exchange is placed.

> 📘 **Price Impact occurs when staking AND unstaking alpha.**

## Slippage from price action

Price impact is predictable from the pool size and your trade size. The **price action** component is not: between submitting your transaction and it landing, other trades in the same pool move the price, so you end up with more or less than you expected. Most of the time this is simply **another random stake or unstake** that happened to land near yours — no one is targeting you.

It *can*, however, be deliberate: an [MEV bot](/docs/mev-shield) that sees your pending transaction and **front-runs** it on purpose to profit from the price move. Because subnet-pool trades are exposed to this, Taostats routes your alpha stake/unstake through **[MEV Shield](/docs/mev-shield)**, which encrypts the transaction so bots cannot read it and front-run you.

## Putting it together

Your total slippage is price impact plus price action. For example, a transaction may have 0.5% price impact on its own, but another trade lands ahead of it and moves the price, adding a further 0.25% — for 0.75% total slippage versus the amount you expected.

## Price Impact & Slippage formulas

The tao/alpha conversion price cannot be used to calculate a transaction.  You must use the following equation to determine the `α_received`:

$$
\alpha_{received} = \alpha_{pool} - \dfrac{k}{tao_{pool} + tao_{staked}}
$$

The opposite occurs when unstaking alpha to buy tao:

$$
tao_{received} = tao_{pool} - \dfrac{k}{\alpha_{pool} + \alpha_{unstaked}}
$$

The amount received will be less than the amount expected from the direct price conversion. That total difference is the slippage (generally shown as a percentage):

$$
Slippage = \dfrac{\alpha_{expected} - \alpha_{actual}}{\alpha_{expected}}
$$

## Price Impact Calculator

<SlippageCalculator />

> 📘 **Example 1 (large purchase = large price impact):**
>
> A subnet pool has 100α and 100τ.  alpha:tao is 1:1, so the alpha price is 1 tao.
>
> <Image border={false} alt="Subnet liquidity pool holding 100 τ and 100 α at a 1:1 ratio" src="https://files.readme.io/b4b5fc63a0c2c45d90bba35e3287ce8a515f79f9440581edfb428297697a1a89-image.png" />
>
> A tao holder wishes to sell 1,000 tao for alpha.  Following the exchange rate of 1:1, you might assume 1,000α would be received. But there is just 100α in the pool, so using the equation above 90.9α is received.
>
> This results in a price impact of 90.91%:
>
> $$
> \dfrac{1000 - 90.9}{1000} \times 100 = 90.91\%
> $$
>
> Large purchases of tao or alpha will have large amounts of price impact.

> 📘 **Example 2 smaller purchase**
>
> A subnet pool has 100α and 100τ.  alpha:tao is 1:1, so the alpha price is 1 tao.
>
> <Image border={false} alt="Subnet liquidity pool holding 100 τ and 100 α at a 1:1 ratio" src="https://files.readme.io/b4b5fc63a0c2c45d90bba35e3287ce8a515f79f9440581edfb428297697a1a89-image.png" />
>
> A tao holder wishes to sell 10 tao for alpha.  Using the equation for alpha\_expected, they will receive 9.09α.
>
> This results in 9.1% price impact.
>
> $$
> \dfrac{10 - 9.09}{10} \times 100 = 9.1\%
> $$

## Price impact and Slippage values

The transaction tables list the actual slippage of a transaction.  A negative slippage means your transaction actually profited from the trade

<Image border={false} alt="Transaction table showing per-trade Slippage % and Fee (τ) columns" src="https://files.readme.io/17ff300d55f73503d339d2de784d3edca266536ebbdb3304891f08701e8dc4e6-image.png" />

## Setting a slippage limit

You can cap how far the price is allowed to move before your stake or unstake is cancelled.  Bittensor provides **limit-price** variants of the staking extrinsics — `add_stake_limit` and `remove_stake_limit` — which take a limit price and **revert with `SlippageTooHigh`** rather than filling if the pool price moves past your tolerance.

> 📘 **Whether a limit is applied depends on the tool**
>
> A slippage limit is **not** enforced by the chain automatically.  The plain `add_stake` / `remove_stake` extrinsics execute at whatever price the pool is at when the transaction lands — no protection.  It is the **tool** that decides whether to route through the limit variant:
>
> * **Taostats** applies a slippage limit to your stake/unstake transactions.
> * **btcli** applies one by default (a 5% tolerance).
> * A tool or script calling raw `add_stake` / `remove_stake` has **no** slippage protection unless it explicitly uses the limit variant.

### Chain minimums and caps

* **Minimum stake:** a single stake below **0.002 tao** (plus the swap fee) is rejected with `AmountTooLow`.
* **Partial unstake floor:** a partial unstake must leave a remainder worth at least **0.002 tao** at the pool price — otherwise unstake the full position instead.
* **Maximum single swap:** on dynamic subnets, a single stake larger than **1000× the pool's tao reserve** is rejected with `InsufficientLiquidity`.  Split very large stakes into smaller transactions.
