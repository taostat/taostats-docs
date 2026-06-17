---
title: Root Reborn
excerpt: >-
  A user-facing explainer for subtensor PR
  [#2759](https://github.com/opentensor/subtensor/pull/2759) _Draft — Last
  updated 2026-06-16. Status: PR open against `devnet-ready`, not on mainnet._
deprecated: false
hidden: false
metadata:
  robots: index
---
## TL;DR

Root dividends still come from selling alpha. But instead of cashing out to root stakers as TAO, the proceeds are immediately re-bought into a basket of subnets chosen by each root validator. Stakers compound in alpha exposure, redeem to TAO on demand.

What changes:

* **Validators pick winners.** Each publishes a weight vector across subnets. That vector is their product.
* **Subnets compete for root buy-flow.** Highly weighted subnets net-buy; unweighted subnets stay at today's net-sell.
* **Stakers' substrate flips.** Root compounded in TAO before (on a declining APY). Now compounds in subnet alpha exposure — variable, validator-dependent, redeemable to TAO any time.

**Status:** Open against `devnet-ready`. Not mainnet yet.

***

## Root reborn calculator

<br />

See how Validator weights effects the returns on root staking compared to present root staking.

https://s3.hippius.com/rufus/public/root-reborn-calculator/index.html

<br />

## 1. What is "root" and why does it have a risk-free rate?

Bittensor has one base subnet, **subnet 0** (root). Everyone who stakes on root holds TAO directly — no per-subnet alpha exposure, no impermanent-loss risk, no betting on a particular subnet's success or failure. In return, root stakers earn a slice of the network's emissions every block.

Because root carries no subnet risk, its yield is the **risk-free rate of the Bittensor economy**: the baseline return any TAO-holder can get just by staking on the safest possible thing. Every other yield in the network — alpha staking on subnet N, providing liquidity, locking for conviction — has to beat root's rate to be worth the extra risk.

But today's "risk-free rate" is **decaying**. Root prop — the fraction of each subnet's emissions earmarked for root — is on a downtrend, recalculated periodically and shrinking as the network matures. Lower root prop = smaller TAO dividend per unit of root stake = lower effective root APY each cycle. So today's risk-free rate isn't a stable floor; it's a slowly eroding one. That decay is one of the structural problems Root Reborn is trying to address — not by changing root prop, but by giving the same dividend stream a more productive substrate to compound in.

***

## 2. The problem today: auto-sell, then leak

Where does root's yield actually come from? Right now, here's the chain of events each block:

1. Subnet emissions mint alpha into every subnet's reward pool.
2. Some fraction of those emissions is owed to **root** as the root proportion (the "root prop" on each pool).
3. The network **sells that alpha back into TAO** through the subnet's AMM pool — every block, automatically. This happens on every subnet that has root proportion, uniformly.
4. The TAO is paid out to root stakers as flat dividends and lands back in TAO circulation.

It works, but it has three real problems:

**(a) Sell is uniform regardless of subnet quality.** Every subnet that mints root dividends gets the same mechanical sell every block. Bad subnets, great subnets, niche subnets — same treatment. Root, the largest pool of stake in the network, has no expression of preference. Yield is paid by treating all subnets identically.

**(b) Root validators are passive.** A root validator in this model is a yield conduit. Stake gets allocated to them, the auto-sell happens, dividends get paid out. The validator doesn't _do_ anything except exist. There's no skill in being a root validator. No allocation decisions. No way to differentiate yourself.

**(c) Yield compounds only in TAO, on a decaying base rate, and proceeds leave the subnet ecosystem.** Auto-sold TAO is added to your root stake (so it does compound). But three problems stack:

* The compounding is purely TAO-denominated — stakers can't express subnet preference.
* The proceeds of _selling alpha_ leave the subnet economy entirely — none of it returns as buy-pressure on any subnet.
* The underlying APY itself is **decaying** as root prop shrinks over time. Each year your effective TAO yield is lower than the last, even though stake count goes up. Compared to other yield systems where yield can be re-deployed into more productive layers, root is a one-way drain on alpha with a declining payout.

***

## 3. The proposal: redirect the proceeds into a chosen basket

Root Reborn keeps the auto-sell on the origin subnet (where the root dividend was minted) and **redirects the resulting TAO into buys across other subnets**:

1. Each root validator publishes a vector of weights `w` across the network's subnets — a list saying "buy 20% into subnet 1, 15% into subnet 5, 10% into subnet 28…" etc. Subnets the validator doesn't list get weight zero.
2. Each block, every root dividend the validator earns (from any subnet) is auto-sold to TAO as today, but instead of being paid to stakers, that TAO is **immediately spent**: buys are placed across the weighted subnets per `w`, and the bought alpha is staked under a special **escrow coldkey** with the validator as the hotkey.
3. The escrow basket compounds. Each block adds more alpha across the weighted subnets. The subnets' own price movements add (or subtract) NAV. The basket keeps growing while it's left alone.
4. Stakers who want their yield in TAO call `root_claim_on_subnet` whenever they like. The system swaps their share of the basket back to TAO through the existing AMM swap, and pays out. Nobody is forced to redeem on a fixed schedule.

**Key point: the sell side doesn't change for the origin subnet.** Every subnet that has root proportion still mints alpha for root and still has that alpha sold to TAO every block, exactly as today. What changes is where the TAO goes next: it used to leave the subnet economy, now it's recycled as fresh buy orders across the basket subnets.

For any individual subnet, the **net effect** is:

* **Sell side:** unchanged from today (your subnet's root proportion is still auto-sold).
* **Buy side:** new — receives buys proportional to how much root capital is allocated to it via weight vectors across all validators.
* **Net:** sell minus buy. Highly weighted subnets net-buy. Unweighted subnets net-sell at exactly today's rate. Mid-weighted subnets land in between.

The mental model: instead of root paying out dividends as a continuous trickle of TAO, root pays you a continuously growing _credit_ in a basket of subnet exposures. You cash in the credit on your schedule, not the chain's.

**Critically, the round-trip is `TotalStake`-neutral.** No TAO is created or destroyed. The alpha that would have been sold is now bought-and-held instead. The accounting is conservation-correct: `Σ (alpha owed to stakers) == BasketPrincipal`.

***

## 4. What changes for each participant

### Root stakers (everyone staking TAO on subnet 0)

**Before:** Your dividends are auto-claimed, swapped to TAO, and added to your root TAO stake. Compounding happens, in TAO, at the protocol layer. But the _rate_ is decaying — root prop is on a downtrend, so the effective TAO APY each cycle is lower than the last. Stake count goes up; the yield it earns per unit gets smaller.

**After:**

* Your dividends are **automatically reinvested into a basket of subnet alpha** chosen by your validator, held under escrow with your validator as the hotkey.
* The basket compounds via three mechanisms: new alpha buys each block (from incoming root dividends), alpha emissions on the basket position (the staked alpha earns subnet rewards), and price action on the alpha held.
* You can redeem at any time via `root_claim_on_subnet`. Redemption is always alpha → swap to TAO → added to your root stake.
* Your effective return is no longer a flat TAO APY — it's whatever the basket NAV grows to. Could outperform pure TAO compounding (good basket, strong subnet performance) or underperform (weak basket, bad subnet picks).
* Your choice of root validator now matters: their basket vector is your portfolio. Picking is real.

**Key shift:** today root compounds in **TAO**; tomorrow root compounds in **subnet alpha exposure**. That's the real change. You gain upside (and downside) from subnet performance instead of a flat TAO yield.

**New consideration:** if you don't want exposure to subnet alpha price swings, redeem more often (each claim returns to TAO root stake). If you're long the network and want compounding subnet exposure, leave it.

### Root validators

**Before:** A passive yield conduit. No skill, no differentiation, no active job. Stakers picked you based on take rate and basic reputation, full stop.

**After:**

* You **set a basket vector** `w` over the network's subnets using a new extrinsic, `set_root_weights`. This is your product.
* Every block, your stakers' dividends flow through _your_ vector. If your picks do well, your stakers compound faster, attracting more stake to you, increasing your take revenue.
* This is a real, ongoing job: research which subnets are productive, watch the network, rebalance, defend your performance publicly.
* **Curation power.** Root stake is a large share of total network stake. A root validator's vector is effectively a stake-weighted vote on which subnets get net buying pressure. Subnets the validator set rates highly get bought; subnets the set rates as bad actors or low-value get starved of buy-pressure.
* Take revenue grows organically when you do a good job — same nominator pool, larger yield base.

**New consideration:** publishing a weak basket vector is now visible and quantifiable. There's nowhere to hide. Good validators will pull stake. Lazy ones will lose it.

### Subnet owners

**Before:** Constant uniform headwind. Every block, a fixed slice of your subnet's emissions is dumped into your AMM pool, driving down your alpha price. Every subnet experiences the same treatment regardless of quality. You're swimming upstream against your own emissions schedule, identically to every other subnet.

**After:**

* The auto-sell on your subnet's root proportion **still happens** (unchanged). Your sell-side pressure from root emission is the same as today.
* **What's new** is the buy side. If your subnet is rated highly by root validators, you receive buys every block proportional to your aggregate weight × the total root dividend flow being recycled.
* **Net for highly-rated subnets:** sell minus buy. If buys exceed sells, your subnet experiences **net buying pressure** for the first time. Real upward pressure on alpha price.
* **Net for unrated subnets:** identical to today's status quo. The sell still happens; no offsetting buy. Neutral change.
* **Strategy shifts:** subnet owners now have an incentive to make their case publicly to root validators. Performance, transparency, useful work all matter more. The validator-set effectively becomes a continuous, capital-allocating jury — with stake-weighted preference, instead of the previous one-size-fits-all sell.
* **The new dynamic:** subnets are competing for root-validator mindshare. Good subnets can attract buy-pressure proportional to their reputation. Mediocre ones default to today's experience.

### Subnet alpha holders / LPs

**Before:** You're on the other side of a uniform auto-sell every block. Net seller pressure on every subnet, all the time.

**After:**

* Sell-side pressure on your subnet is **unchanged**.
* Buy-side pressure appears proportional to how much weight your subnet gets from root validators.
* **Net effect on alpha prices:**
  * **Highly weighted subnets:** tighter floors, possibly net upward pressure.
  * **Unweighted subnets:** unchanged from today.
  * **Mid-weighted subnets:** dampened sell pressure but not eliminated.
* LP economics improve on weighted subnets because the new buy-side activity creates real two-sided flow against your LP, not just protocol-mandated dumps.

### TAO holders generally

**Before:** Root yield compounded in TAO at the protocol level (auto-sold alpha became added root stake). The compounding worked, but the alpha sales fed nothing back into the subnet economy — the network was strictly a sink on alpha.

**After:**

* The auto-sell still happens, but the TAO is immediately re-spent on alpha buys across the basket subnets. None of it sits idle.
* Root yield compounds in **alpha exposure** instead of in **TAO stake**. Net root capital base grows in subnet-alpha terms, not in TAO terms.
* Network-wide effect: alpha that previously was sold-then-stuck-as-staked-TAO is now sold-then-bought-back-as-staked-alpha. The subnet economy gets buy-flow it didn't before.
* The expected return on root may rise (if median basket beats flat TAO compounding) or fall (if baskets underperform).
* **Net effect: subnet economy receives net buy-flow it didn't before; root return is now coupled to subnet performance rather than independent of it.**

***

## 5. How the new system actually works

For readers who want the mechanics. The rest of you can skip to section 6.

### The basket vector

Each root validator gets a uid in the root subnet. The basket vector `w` is stored under the **existing** root-weights map (`Weights[ROOT][uid]`) — the dormant root-weights plumbing is being revived rather than introducing a new storage map. Because it's uid-keyed, the basket follows the validator through hotkey swaps automatically.

Validators set `w` via a new dedicated extrinsic, `set_root_weights`. The generic `set_weights` extrinsic doesn't work here because it rejects netuid 0 — and root needs slightly different validation rules (no Yuma consensus runs on root; weights are used purely as an allocation vector, not as a consensus signal).

### The block-step pipeline

Each block, the coinbase replaces `run_auto_claim_root_divs` with `distribute_root_alpha_to_basket`. For each root validator with a non-zero stake and a non-zero `w`:

1. Sell origin alpha → TAO (same AMM path as before).
2. For each subnet `i` with weight `w[i] > 0`: buy alpha in subnet `i` with `w[i]` share of the TAO.
3. Stake that alpha under the **global escrow coldkey** with the validator as hotkey.
4. Record the principal: `BasketPrincipal[validator] += TAO_spent`.
5. Bump the per-staker claimable rate so each staker's share of the basket is tracked correctly.

If the validator has no weights set, or no root stake, the alpha is recycled (returned to the emission pool) — no broken state. The whole step is transactional: either all the buys succeed or the block step is rolled back for that validator.

### Redemption

Stakers redeem with `root_claim_on_subnet`. The payout formula:

```
payout = owed_principal × (escrow_value / BasketPrincipal)
```

That ratio captures all compounding — both new alpha buys, alpha emissions on the basket position, and price appreciation — in a single shared multiplier. The last staker to redeem can't over-draw because the invariant `Σ owed == BasketPrincipal` is maintained by every block-step.

**Claim granularity:** each call to `root_claim_on_subnet` is scoped to one (validator, subnet) pair and redeems your entire owed principal on that slot — not partial. But because slots are independent, you can claim just your SN1 exposure with validator X (leaving SN5 with X compounding, and your slots with validator Y untouched). A convenience extrinsic `root_claim` iterates over every (validator, subnet) slot for the caller, for full-exit.

**Redemption is always to TAO.** The PR removes the legacy `Keep` claim type — every claim now goes alpha → swap to TAO → added to root stake. No "keep as subnet alpha" path remains. If you want subnet alpha exposure on your coldkey, you must claim to root TAO, unstake, then stake into the subnet manually.

Auto-claim is **removed**. The old `run_auto_claim_root_divs` block-step is gone. No more forced-redemption schedule.

### Hotkey swaps and subnet dissolves

* **Hotkey swap:** the validator's escrow basket positions, `BasketPrincipal`, and root-weight vector migrate to the new hotkey. The basket follows the validator by value.
* **Subnet dissolve:** when a subnet is dissolved, baskets are liquidated back to TAO and paid out to root stakers before teardown. Nobody loses their share to a subnet death.

### Migration

A one-shot migration, `migrate_seed_beta_basket`, seeds the new model from legacy state. Existing `RootClaimable` slots are converted into escrow entries with `E = P = remaining`, preserving every staker's outstanding claim. The migration is conservation-correct: nothing is re-minted, nothing is lost.

### New RPC views

For wallets and dashboards (Taostats, included):

* `betaBasket_getStakerOwed(coldkey)` — pending TAO owed to a specific staker
* `betaBasket_getValidatorNav(hotkey)` — current NAV of a validator's basket
* `betaBasket_getValidatorBasket(hotkey)` — basket composition (per-subnet alpha holdings)
* `betaBasket_getTotalNav()` — network-wide root NAV, mark-to-market

This is everything Taostats needs to render: per-validator basket performance, per-staker pending TAO, network-wide root health.

***

## 6. Why this is structurally important

Four properties make Root Reborn worth taking seriously, beyond the obvious recycling of yield into the subnet ecosystem:

### Validators become curators

Until now, the only way to express "I think subnet X is overrated" was at the individual staker level — and most stakers don't have the bandwidth, expertise, or stake size to make that call meaningfully. Root Reborn lets **root validators** make that call on behalf of their stakers, in a stake-weighted way, every block, with their own performance visible.

This turns the validator set into a continuous, capital-allocating market. Bad actors don't need to be voted off by governance; they just don't show up in root validators' weight vectors, and the buy-pressure machinery starves them. Good subnets get bought into. Network curation becomes emergent, not legislated.

### Subnet differentiation

Today every subnet faces the same auto-sell, regardless of merit. The protocol expresses no preference — a great subnet and a fading subnet experience the same root-emission headwind block after block.

After Root Reborn, that uniform treatment ends. Each subnet's _net flow_ (sell minus buy) becomes a function of the validator set's collective judgment. Subnets earn or lose root buy-pressure based on how root validators rate them — and the rating shows up immediately, every block, in price action and LP economics. This is the strongest gradient between "good" and "weak" subnet performance the network has ever had at the protocol level.

### Compounding flywheel

Today root yield compounds in TAO at the protocol layer — it works, but the underlying rate is decaying (root prop shrinks), and the proceeds (sold alpha) leave the subnet economy entirely. Two-sided erosion: yield rate down, no contribution back to subnets.

Tomorrow root yield compounds in subnet alpha exposures that stay in the subnet economy. The dividend stream the validator receives is still subject to root prop decay — but it's now invested into productive subnet positions that themselves earn emissions and (potentially) appreciate. So even on a declining root prop, the basket can earn back through subnet emissions, price action, and the second-order effect of helping subnets it weights highly.

If the median basket beats flat TAO compounding on a declining root prop (which is the bet — subnet emissions on basket positions plus price appreciation should exceed the eroding pure TAO yield), effective root returns rise relative to the TAO-only path. Higher effective return → more capital flows to root → more recycling → more buy-pressure on weighted subnets → healthier subnets emit more → bigger root dividends → higher effective return. Flywheel.

The flip side: if subnets collectively shrink, baskets shrink with them. Root is no longer pure TAO exposure; it now carries subnet-alpha exposure between claims. That's a real change in risk profile — root is "lower risk than any single subnet" but no longer "pure TAO compounding." Stakers who want pure TAO exposure should redeem more frequently.

### Survives without governance

The whole mechanism rides on machinery that already exists. `RootClaimable` was already basket-shaped — Root Reborn just feeds it differently. Share pools, AMM swaps, hotkey-swap hooks, subnet-dissolve hooks all reuse existing code. The new surface area is small: one redirected emission call, one new extrinsic (`set_root_weights`), one new claim function, and four RPC views.

Most network-wide changes need extensive governance and migration plans. This one is essentially a redirect.

***

## 7. What's known to be incomplete

Per the PR's own "known follow-ups" section, these are not blocking devnet but will be addressed before mainnet:

* Vestigial auto-claim code (`run_auto_claim_root_divs`, `StakingColdkeys*` indexing, ignored `RootClaimType`/`set_root_claim_type`) still needs to be removed.
* **Weight-metering** of the basket fan-out in the coinbase. Right now the AMM work each block is unmetered — needs caps before mainnet scale.
* **Slippage / self-deal guards** on the weight vector `w`. A validator could in principle set a vector that buys into shallow pools they LP into. Slippage caps and self-deal limits are coming.
* Dissolve liquidation should be pro-rata by `owed` rather than current root share (a minor fairness fix).
* The seed migration is currently single-block — needs to be multi-block before mainnet because of scale.
* Clearing `Weights[ROOT][uid]` on root UID reassignment, so a recycled UID doesn't inherit the prior validator's vector.
* **Root `WeightsRateLimit` must be configured.** Today the root subnet's weight rate-limit is `u64::MAX` — effectively disabling weight-setting on root. For Root Reborn to function, sudo must set a real value before/at mainnet activation. The PR doesn't ship a migration setting it; this will be a separate operator action. The chosen value determines how often validators can rebalance their basket vectors (too tight → can't respond to subnet events; too loose → easier MEV target).

None of these are economically broken — they're production-hardening items. Devnet runs are about validating the core mechanism, not these edges.

***

## 8. What this means for Taostats users

Taostats already shows per-pool prices, validator performance, and staker positions. Once Root Reborn lands on mainnet, three things become first-class metrics worth surfacing:

**(a) Root validator performance, ranked.** A new dimension beyond take rate and reputation: **basket NAV per unit stake**, over various windows (1d / 7d / 30d). This is the ROI of picking a particular root validator. Surfacing this clearly will move stake toward the active managers and away from the lazy ones.

**(b) Basket composition.** Per root validator: "this validator is allocating X% to SN1, Y% to SN5, Z% to SN28…" Investors care about transparency.

**(c) Per-staker pending TAO.** Stakers need an easy way to see "if I redeemed right now, I'd get X TAO." The `betaBasket_getStakerOwed` RPC is exactly that, ready to render on portfolio pages.

We should plan to ship these views shortly after mainnet activation. If we're early on the data layer we'll be the default place root stakers go to evaluate their validator choice — and that's a high-engagement audience.

***

## 9. Open questions

Worth flagging for community discussion:

* **Root weight rate limit — hourly, daily, weekly?** Validators rebalance their basket vectors via `set_root_weights`, which is governed by the root subnet's `WeightsRateLimit`. Currently set to `u64::MAX` (effectively disabled). Before mainnet activation sudo must set a real value, and the choice has real consequences:
  * **Hourly (e.g. 300 blocks):** validators can react quickly to subnet performance changes, but bots can easily front-run published rebalances, and stakers see constant churn in their exposure. MEV-friendly.
  * **Daily (e.g. 7,200 blocks):** middle ground. Validators can respond to meaningful subnet events within a day. Less MEV surface, but a validator can't quickly react to a sudden subnet collapse or surge.
  * **Weekly (e.g. 50,400 blocks):** validators must take longer-horizon views. Vectors become more like investment theses than tactical positions. Hardest to MEV. But a fast-changing subnet event can leave stakers locked into a now-stale allocation for days.
  * The PR doesn't specify and doesn't include a migration to set it. This needs a community decision before mainnet — it materially shapes how validators position themselves and how stakers evaluate them.
* **Slippage caps:** how strict before they distort allocation? Too loose and a validator can manipulate shallow pools; too tight and they can't allocate to small but legitimately rated subnets.
* **Default basket for validators who don't set one:** currently no weights = recycled emissions. Should the protocol provide a sane default (e.g., equal-weight over top-N subnets)? Or force validators to publish?
* **Front-running:** if basket vectors are publicly visible (they will be, on-chain), can MEV actors front-run rebalances? Probably yes for naive implementations. The root `WeightsRateLimit` setting partially mitigates this — lower frequency rebalances are easier to defend than per-block ones. The exact rate-limit value remains an open operator decision.
* **Loss of `Keep` claim option:** the previous ability to claim root dividends as subnet alpha (rather than swap-to-TAO) is removed by this PR. Stakers who specifically wanted to compound into a single subnet via their validator's allocation lose that path. Is the simplified UX worth the lost flexibility? Open question.
* **Validator collusion:** a coordinated group of large root validators could collectively starve a subnet by zeroing it from all their baskets. That's actually a feature (network curation) if the subnet is bad, but a bug if it's targeted abuse of an honest competitor. No on-chain remediation in the current design — relies on validator-set decentralization.

***

## 10. Recap

| Before                                                                                                       | After                                                                                                                                                            |
| ------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Auto-sell every block on every subnet, uniformly                                                             | Auto-sell unchanged on origin subnet, but TAO proceeds are recycled as buys across chosen subnets                                                                |
| Sell proceeds exit the subnet economy entirely (TAO added to root stake)                                     | Sell proceeds stay in the subnet economy as new alpha buys, compounded under the validator                                                                       |
| Every subnet treated identically by root                                                                     | Each subnet's net flow depends on root validator weight — strong subnets net-buy, ignored subnets stay at today's net-sell                                       |
| Root validators passive yield conduits                                                                       | Root validators are active capital allocators with a public, ranked basket vector                                                                                |
| Root yield compounds **in TAO** at the protocol layer, on a decaying base rate (root prop shrinks over time) | Root yield compounds **in subnet alpha** as a validator-chosen basket, with subnet emissions and price action providing potential offset to the underlying decay |
| No subnet curation by validators                                                                             | Continuous stake-weighted capital-allocation vote on subnet quality                                                                                              |
| Risk-free rate is a slowly eroding TAO APY                                                                   | Effective return depends on basket performance — can outperform or underperform the eroding TAO-only path                                                        |

**Status:** PR open against `devnet-ready`, not on mainnet. Authored by `unconst` + Cursor. 17 files modified, 1,177 unit tests passing, two independent reviews completed with both findings fixed. Mainnet deployment will follow normal `devnet-ready → testnet → mainnet` progression with the items in section 7 resolved first.

If you want to read the source: [opentensor/subtensor#2759](https://github.com/opentensor/subtensor/pull/2759).
