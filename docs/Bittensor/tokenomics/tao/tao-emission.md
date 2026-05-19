---
title: 'Tao Emission '
excerpt: Basics on how tao is emitted and distributed in Bittensor.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Every block, 0.5 tao is emitted by the chain (the first [Halving](doc:halving) was in December 2025).  Where do these tokens go?

<br />

The tao is divided amongst the subnets based on emission.  And, then, depending on the alpha price, some is injected into the liquidity pool, and some is used as a chain buy to purchase alpha (that is then recycled).

# How emission is determined

Net tao flow is used to determine emission.  This is a new parameter being introduced in May 2026 (tao flow was introduced in early 2026). It now has its own page [Tao Flow](doc:tao-flow)

The tao flow is normalized, and the tao emitted to each subnet subnet is based on the normalized net flow flow.

Emitted tao has 2 destinations:

* tao injected
* chain buy

## Tao injected

This is the primary feature of tao emission.  Tao from the chain is injected into the subnet's liquidity pool.  An equal amount of alpha is minted and created at the same time (in order to keep the liquidity pool and the price balanced.

However, there is a limit of 0.5 alpha that can be injected into the pool per block.  This means that the tao injected is max(emitted, price*0.5).

## Chain Buy

If tao injected is limited by the alpha price, there is excess tao that was emitted to the subnet.  This tao is used to buy alpha, an dthen the alpha is recycled.  This mechanism raises the alpha price - eventually leading to the chain buys stopping.

<Callout icon="📘" theme="info">
  Example

  Subnet 44 has emission of 12%, and a price of 0.04258.

  Only 0.02129 can be injected because of the price and alpha_in being injected.  This leaves 0.03841τ that is used to buy alpha and recycle it.

  * 12% emission of 0.5 tao =                 0.0597τ
  * max tao injected = 0.5α * .04258 =  0.02129τ
  * Excess Tao:                                          0.03841τ
</Callout>

<br />

## Owner Emission Toggle

Starting in May 2026, subnet owners can turn off emission into their pool with:

`SubnetEmissionEnabled(netuid)`

When False, tao emission is zeroed (no alpha_in, no chain buys).  The alpha_in is also stopped.  Alpha_out emission continues unchanged.

<br />

<br />

<br />

<br />
