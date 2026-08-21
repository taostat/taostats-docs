---
title: Runtime 447 (release v447)
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

The Bittensor mainnet runtime upgraded to **spec version 447**. Unlike the bundled [runtime 445](/docs/runtime-445) release, v447 is a single-feature change: it retunes the **conviction-based subnet-ownership takeover rule** (the [subnet king](/docs/#7-subnet-king-mechanism) mechanism), replacing a subnet-wide 10% quorum with an 18% bar on a single hotkey.

> 📘 **Live on mainnet (spec 447)**
>
> Confirmed on-chain: runtime version **447** activated at block **8,844,992** (2026-08-14 19:44 UTC on Finney), read from the Taostats [runtime version](/api-reference/chain/get-runtime-version-latest/) index.

## The short version

- **Ownership now transfers on one hotkey's own conviction, not the subnet-wide total.** Before v447, a subnet's ownership moved to the highest-conviction hotkey once the **total** rolled conviction across the whole subnet (every hotkey and coldkey, including the incumbent owner) reached **10% of eligible alpha**. From v447, ownership transfers only when a **single hotkey's own rolled aggregate conviction exceeds 18% of eligible alpha, by itself**.
- **The subnet-wide sum no longer counts.** Other keys' locks — including the owner's — no longer add to a challenger's threshold. Only conviction locked toward the winning hotkey counts toward its bar.
- **Everything else is unchanged.** Eligible alpha is still `SubnetAlphaOut − SubnetProtocolAlpha − AlphaBurned` (saturating at zero), the subnet must still be at least `ONE_YEAR` (2,629,800 blocks) old, and a zero eligible balance still cannot trigger a transfer.

## Why the rule changed

Summing conviction across every locker meant unrelated stakers — and even the incumbent owner's own locked alpha — could inadvertently supply a challenger's quorum. A subnet could cross the 10% subnet-wide bar without any single party actually committing enough conviction to warrant taking ownership.

v447 closes that path by measuring only the **winning hotkey's own conviction**. Coalitions still work exactly as before: backers who want to support a challenger lock directly to that challenger's hotkey, so their conviction lands in that hotkey's own aggregate and counts toward the 18% bar. What no longer counts is conviction locked elsewhere on the subnet.

## What actually changed in the gate

Both the winner selection and the admission check now run through one shared computation (`subnet_king_with_conviction`), so the gate can never disagree with the hotkey it examined:

- **Before (spec 446):** `get_total_conviction(netuid) × 10 ≥ eligible_alpha` — a subnet-wide sum against a **10%** bar (`≥`).
- **From spec 447:** `king_conviction × 100 > eligible_alpha × 18` — the **single winning hotkey's** conviction against an **18%** bar, strict (`>`). The comparison is cross-multiplied in 256-bit integers over the raw `U64F64` bits so a high-range takeover can't saturate and get wrongly rejected.

The full mechanism — how conviction is rolled forward per hotkey, how the aggregate buckets swap on transfer, and the worked numbers — is documented in the [Conviction](/docs/conviction-v2) concept page.

## What this means

- Any estimate of when a subnet becomes takeover-eligible must now project a **single hotkey reaching 18% of eligible alpha on its own**, not the subnet-wide total reaching 10%. In practice this raises the effective bar for a takeover on most subnets, because the incumbent owner's and unrelated stakers' locks no longer contribute.
- Tools and dashboards that surfaced "subnet-wide conviction vs. 10%" as a takeover-readiness signal are now measuring the wrong quantity; the readiness signal is the **leading hotkey's own conviction vs. 18%**.

## Source provenance

- **Release:** [`RaoFoundation/subtensor` v447](https://github.com/RaoFoundation/subtensor/releases/tag/v447), single PR [#3083](https://github.com/RaoFoundation/subtensor/pull/3083) ("Conviction normalization: single-hotkey 18% takeover gate").
- **On-chain confirmation:** runtime version **447** at block **8,844,992** (2026-08-14 19:44 UTC), Finney, via the Taostats runtime-version index.
- **Gate (verified at `v447`):** `pallets/subtensor/src/staking/lock.rs` — `change_subnet_owner_if_needed` (L1180) gates on `king_conviction × 100 > eligible_alpha × 18`, where `king_conviction` comes from `subnet_king_with_conviction` (L1093, the winning hotkey's rolled aggregate). Compared against `v446`, which gated on `get_total_conviction(netuid) × 10 ≥ eligible_alpha` (subnet-wide sum, 10%). `eligible_alpha` and the `ONE_YEAR` age gate are byte-for-byte unchanged between the two tags.

> 📘 The v447 release train lives on the `RaoFoundation/subtensor` repository (the former `opentensor/subtensor`, now redirected). PR numbers reference that repository.

See also: [Conviction](/docs/conviction-v2) ·
[Runtime 445](/docs/runtime-445) ·
[Protocol changes overview](/docs/protocol-changes)
