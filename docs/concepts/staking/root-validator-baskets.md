---
title: What changed
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

Root Validator Baskets are the mechanism [Root Reborn](/docs/shorting-explainer) introduced for handling root dividends. They are live on mainnet (subtensor `spec_version` 441).

For the full tiered treatment — per-participant impact, mechanics, and open questions — see the [Root Reborn explainer](/docs/shorting-explainer) and its [TL;DR](/docs/tldr). This page is the short canonical reference.

Before Root Reborn, root dividends were auto-sold from alpha to TAO and compounded onto your root stake automatically. Root stakers chose how to receive rewards through "keep vs. swap" claim options. **Both of those are gone.** There is no auto-claim, no "keep as alpha" path, and no keep/swap toggle.

Now, each root validator curates a **basket**: root dividends are re-bought into a set of subnets the validator chooses, and held as compounding subnet-alpha exposure until you redeem to TAO.

# The basket vector

Each root validator publishes a **weight vector** `w` across the network's subnets — for example "buy 20% into subnet 1, 15% into subnet 5, 10% into subnet 28…". Subnets the validator doesn't list get weight zero.

* Validators set `w` with a dedicated extrinsic, `set_root_weights`. (The generic `set_weights` rejects netuid 0.)
* The vector is the validator's **product**. Stakers pick a validator on its basket performance, not just its take rate.
* A validator that sets **no** vector buys nothing — its stakers earn no root reward that cycle. There is no default basket by design.

# How rewards accrue

Each cycle, for every root validator with stake and a non-zero vector:

1. The origin subnet's root dividend is **auto-sold to TAO** — same as before Root Reborn. The sell side on any subnet is unchanged.
2. That TAO is **immediately re-bought** across the weighted subnets per `w`.
3. The bought alpha is staked under a global **escrow coldkey** with the validator as hotkey, joining the validator's single basket **fund**.
4. Your deposit mints **fund shares** at the pre-deposit net asset value (NAV). Your slice of the basket is tracked as a share balance.

The basket compounds three ways: fresh alpha buys each cycle, alpha emissions on the basket's positions, and price movement on the alpha held. The round-trip creates and destroys no TAO — it is `TotalStake`-neutral.

# Redeeming: claim_root

Your balance no longer rises on its own. To realise rewards you make a single manual `claim_root` call:

* It takes **no arguments**. It sweeps **every validator you currently have root stake with** at once — you can't cherry-pick one basket or one subnet.
* Your shares are valued at the fund's current NAV and redeemed **pro-rata across all holdings**, swapped to TAO, and staked back onto root.
* Redemption is **always to TAO**. There is no "keep as subnet alpha" option; if you want subnet alpha on your coldkey, claim to root, unstake, then stake into the subnet yourself.
* A validator you've **fully exited** (zero stake) is skipped — its basket stays parked until you re-stake, not swept.

# Costs and considerations

* **Claiming costs a fee** that scales with how many subnets the validator's basket holds. The chain **reserves up to ~0.115 TAO** up front — the worst-case envelope for a basket at the 256-holding cap — and you must have that much free to submit the claim. It then **refunds down to your basket's actual width**, so what you permanently pay tracks how many subnets the basket really touches, not the ceiling:

  | Basket holdings | Fee actually paid |
  |---|---|
  | 8 | ~0.0036 TAO |
  | 128 | ~0.057 TAO |
  | 256 (cap) | ~0.115 TAO |

  A narrow basket costs a small fraction of the reservation; only a basket at the cap pays the full ~0.115. Claim infrequently, and prefer a validator with a **concentrated** basket. (A Root Reborn claim only touches the validator's basket — far cheaper than a pre-Root-Reborn root claim, which settled across all subnets.)
* **Switching validators — claim first.** Your basket entitlement is tied to the root stake delegated to *that* validator. If you move or unstake without claiming, your claimable on the old basket drops toward zero (nothing is burned — re-staking the same amount restores your claim, minus the compounding you missed).
* **Your return now depends on subnet performance.** Root used to be flat TAO compounding on a decaying rate. Between claims you now hold subnet-alpha exposure — it can outperform or underperform. Stakers who want pure TAO exposure should claim more frequently.

# Data on Taostats

Root Reborn exposes a `BetaBasketRuntimeApi` with views for per-staker owed TAO, per-validator NAV and basket composition, network-wide root NAV, and each validator's weight vector. These power basket performance, composition, and pending-claim metrics on Taostats.

# Related

* [Root Reborn — full explainer](/docs/shorting-explainer)
* [Root Reborn — TL;DR](/docs/tldr)
* [Stakeholder Emissions: Root](/docs/stakeholder-emissions-root)
* [Dividends for Validators](/docs/dividends-for-validators)
* [Staking in dTao](/docs/staking-in-dtao)
