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

## Triumvirate

The triumvirate can toggle tao emission on and off.  This is done when the chain leadership has determined that the subnet is not providing value.  This can be retrieved in the get Subnet pools API endpoint:`"subnet_emission_enabled": false`.

When tao emission is halted - alpha_in is also halted.

## Chain emission

`Updated in chain spec 421 on June 23, 2026`

If the subnet is allowed to retrieve emission, emission is determined by 3 factors:

* **Price**: the EMA price on chain
* **Root prop**: the subnet's Root proportion (see [Emissions: Root vs. Alpha Stake](doc:stakeholder-emissions-root-vs-alpha))
* **Miner Burn**: How much of the miners incentive is burned

![](https://files.readme.io/ee90fb0af505425b56c1fbcb9e11ad402e7be32a1fd44449181863a5a1ee0ba4-image.png)

This is normalized across all subnets to 100%.

Emitted tao has 2 destinations:

* tao injected
* chain buy

## Tao injected

This is the primary feature of tao emission.  Tao from the chain is injected into the subnet's liquidity pool.  An equal amount of alpha is minted and created at the same time (in order to keep the liquidity pool and the price balanced.

However, there is a limit of alpha that can be injected into the pool per block.  This was changed to `alpha_emission * root_prop` in June 2026.

* Alpha Emission: 1 for all subnets until 2028/2029 when alpha halvenings begin.
* The alpha_in cap is essentially root_prop

This means that newer subnets (higher root prop) have higher amounts of tao injected into the pool.  Older subnets (presumably with larger pools) get less, but more chain buys.

## Chain Buy

If tao injected is limited by the alpha price, there is excess tao that was emitted to the subnet.  This tao is used to buy alpha, an dthen the alpha is recycled.  This mechanism raises the alpha price - eventually leading to the chain buys stopping.

<Callout icon="📘" theme="info">
  Example

  Subnet 44 has emission of 12%, root_prop= 50%, and a price of 0.04258.

  Only 0.02129 can be injected because of the price and alpha_in being injected.  This leaves 0.03841τ that is used to buy alpha and recycle it.

  * 12% emission of 0.5 tao =                 0.0597τ
  * max tao injected = 0.5 * .04258 =  0.02129τ
  * Excess Tao:                                          0.03841τ
</Callout>

<br />

<br />

<br />

<br />

<br />

<br />
