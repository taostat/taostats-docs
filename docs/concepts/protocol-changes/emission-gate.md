---
title: The emission gate (spec 440)
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

> 📘 **Live on mainnet (spec 440)**
>
> This change is **live on mainnet** — spec version **440**, confirmed on Finney
> via `state_getRuntimeVersion`. The figures below are a point-in-time snapshot
> (block 8,714,269, 2026-07-27) and will drift as demand and the bar θ move.

## The short version

Every block, the chain hands out TAO emission and each subnet competes for a
slice. **Until spec 440, a subnet's slice was simply proportional to how much
the market wanted it** — twice the demand earned twice the emission. Spec 440
adds a **gate**: it draws a line, lets the sought-after subnets keep their full
slice, chokes the barely-wanted ones toward zero, and hands the freed-up
emission back up to the top.

How "wanted" a subnet is — its **demand** — is measured exactly as before. Only
how that demand turns into emission changed.

> 📘 **What was the answer is now an input**
>
> The quantity `price × (1 − miner_burned)`, renormalized — which our
> [price-based emission shares](/docs/price-based-emission-shares)
> page described as *the* emission share — is now the **demand `s`**: the identical
> math, but used as the **input** to the gate instead of being the final answer.

## 1 · Building demand (`s`) — same math as before

Demand is built in three steps, unchanged from the price-based-shares design:

- **Step A — price.** Each subnet's raw demand is its **moving alpha price** —
  the EMA of its alpha token's price against TAO from the AMM pool
  (`get_moving_alpha_price`). Staking TAO into a subnet's pool bids its price up:
  higher price = more demand. Because it's an EMA, a one-block spike can't game it.
- **Step B — normalize into a share.** Divide each subnet's price by the sum of
  all prices → shares that sum to 1: `sᵢ^price = movingPriceᵢ / Σⱼ movingPriceⱼ`.
- **Step C — discount for miner burn, renormalize.** Scale each share by
  `(1 − miner_burned)` and renormalize:
  `sᵢ = sᵢ^price·(1 − minerBurnedᵢ) / Σⱼ sⱼ^price·(1 − minerBurnedⱼ)`. A
  full burner → 0. The result is the **demand share `s`** that feeds the gate.

Miner burn is a heavy first-stage filter, not a footnote: in the 2026-07-27
snapshot, 35 of 128 subnets burned 100% of their miner emission (zeroed out
before the gate even sees them), 32 burned partially, and mean burn network-wide
was ~43%.

## 2 · The bar (θ) — where the line sits

**θ ("theta")** is a **q-mass quantile** on demand, recomputed every **360
blocks**:

1. Sort all subnets' demand shares **largest → smallest**.
2. Walk down, accumulating the shares.
3. The moment the running total crosses **q = 0.61** (61% of all demand), stop.
   The share you're standing on is **θ, the bar**.

Because shares sum to 1, "cumulative ≥ 0.61" means the top subnets together own
61% of demand. θ is a property of the demand **distribution**, not the subnet
count — spinning up empty subnets adds no demand, so it can't move the bar.

## 3 · The gate — a Hill function

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/0bbf18f1dbf03958.png" />

The two forms are identical; the chain computes the right-hand one because `s^h`
underflows fixed-point precision for deep-tail shares, while the ratio `θ/s`
stays well-conditioned. `h` (default **3**, sudo-settable 1–8) sets how sharp the
cliff is. The gate returns a number in `[0, 1]`:

| Your demand `s` vs bar θ | gate(s) | Result |
| --- | --- | --- |
| well above θ | → 1.0 | keep ~all your emission |
| exactly at θ | 0.50 | keep exactly half |
| well below θ | → 0.0 | emission choked toward zero |

### Then: renormalize (the redistribution)

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/9565ef47c55331a5.png" />

Gating shrinks every share, but the block still emits a fixed total. Dividing by
the new (smaller) sum scales the survivors back up — this is how the tail's lost
emission flows to the winners. **A top subnet ends up emitting more than its raw
demand share.**

### Then one more redistribution — emission-enabled subnets only

After the gate, the chain checks **`SubnetEmissionEnabled`** for each subnet. Any
subnet with it set to `false` has its gated share **zeroed and redistributed to
the enabled subnets** (a second renormalize over the enabled set only). This is a
**separate switch from miner burn** — a subnet can clear every filter, survive
the gate, and still be zeroed here. It's the final stage, and it's why the live
emission a subnet actually receives is slightly higher than the gate alone would
give.

## 4 · What it means

- **Emission is no longer proportional to demand.** Any APY or emission figure
  that assumes a pro-rata split is now wrong for every subnet — winners are
  understated, the tail overstated.
- **The tail gets crushed.** In the snapshot, ~38% of demand (below-bar subnets)
  collectively earned ~10% of emission. A low-demand subnet's emission — and its
  miners'/validators' yield — drops sharply.
- **Miner burn is a first-stage filter.** Before the gate runs, `(1 − miner_burned)`
  zeroes or shrinks a subnet's share. Any model that ignores burn will misplace
  which subnets earn.
- **The bar moves.** θ recomputes every 360 blocks from live prices, so which
  subnets are "above the line" shifts as demand shifts. A static calculation
  will drift.
- **Two sudo knobs.** `q` (default 0.61, bar height) and `h` (default 3, cliff
  sharpness) are both root-settable — a governance change to either reshapes
  every subnet's emission at once.
- **A separate emission-enabled switch runs last.** After the gate, any subnet
  with `SubnetEmissionEnabled = false` is zeroed and its share redistributed to
  the enabled subnets. It's independent of demand, burn, and the gate — a subnet
  can survive everything else and still earn nothing.

## Source provenance

- **Code:** `pallets/subtensor/src/coinbase/subnet_emissions.rs` (v440 tag):
  `get_subnets_to_emit_to` / `get_shares` / `maybe_update_emission_gate_bar` /
  `apply_emission_gate` / `get_subnet_block_emissions`.
- **Spec:** runtime version confirmed **440** on Finney (mainnet) via
  `state_getRuntimeVersion`.
- **Snapshot:** demand = moving alpha price × (1 − miner burn), read off-chain at
  block **8,714,269** (2026-07-27 15:51 UTC), q = 0.61, h = 3, 126 emit-set
  subnets. θ landed at rank 18 (SN83), 1.339%. Reconciles to the live per-subnet
  emission Taostats displays (e.g. SN64 = 16.63% vs 16.67%).

See also: [Price-based emission shares](/docs/price-based-emission-shares) ·
[Tao Emission](/docs/tao-emission) ·
[Subnet Emissions](/docs/subnet-emissions)
