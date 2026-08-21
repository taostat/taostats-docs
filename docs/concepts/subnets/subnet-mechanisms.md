---
title: Subnet Mechanisms
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

Each subnet can run multiple **mechanisms** (formerly called sub-subnets), allowing one subnet to work on several distinct challenges. This page covers how a subnet owner divides the subnet's `alpha_out` across those mechanisms.

For how `alpha_out` is then split among subnet owner / miners / validators inside a single mechanism, see [Subnet emission overview](/docs/split-alpha-out). For the broader emission flow, see [Subnet Emission: tao and alpha](/docs/subnet-emissions).

## Mechanisms in a subnet

In V1 of subnet mechanisms, all miners and validators in a subnet compete in every mechanism. The owner sets how the subnet's per-block `alpha_out` is split across mechanisms via:

```rust
pub fn sudo_set_mechanism_emission_split(
    origin: OriginFor<T>,
    netuid: NetUid,
    maybe_split: Option<Vec<u16>>,
) -> DispatchResult
```

The `maybe_split` vector defines the percentage of subnet emission that flows to each mechanism.

> 📘 **Split examples**
>
> * Two mechanisms, even split: `50:50`.
> * Two mechanisms, one is new and ramping up: `90:10`.

A subnet may host up to 8 mechanisms (2 at launch, rising to a ceiling of 8).

## How mechanism splits feed participant rewards

Inside each mechanism, the standard split applies (owner / miners / validators). Rewards for an individual miner or validator are calculated **per mechanism** and then aggregated to the subnet level using the mechanism-split weighting.

Concretely:

* A miner's `incentive` and a validator's `dividend` are computed inside each mechanism.
* Each mechanism contributes to the participant's subnet reward in proportion to its share of the split.
* The summed result is what the participant earns from the subnet per tempo.

See:

* [Subnet emission overview](/docs/split-alpha-out) — the canonical map of how `alpha_out` is split inside a single mechanism.
* [Consensus for miners](/docs/consensus-for-miners) — how `incentive` is awarded inside a mechanism.
* [Dividends for Validators](/docs/dividends-for-validators) — how `dividend` is awarded inside a mechanism.
