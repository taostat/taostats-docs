---
title: Runtime 445 (release v445)
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

The Bittensor mainnet runtime upgraded to **spec version 445**. Unlike the single-feature explainers elsewhere in this section, v445 is a bundled release: it reworks transaction-fee handling, restores miner-burn emission scaling, expands the EVM precompiles, and adds Ledger-style signatures for limit orders, alongside a set of storage-hygiene and proxy/multisig fixes.

> 📘 **Live on mainnet (spec 445)**
>
> Confirmed on-chain: runtime version **445** activated at block **8,831,003** (2026-08-12 21:06 UTC on Finney), read from the Taostats [runtime version](/api-reference/chain/get-runtime-version-latest/) index. Mainnet went straight from 443 to 445 — spec 444 was never a live mainnet runtime.

## The short version

- **Transaction fees are recycled, not paid to block authors.** v445 reverts the earlier "reward the block author" behaviour: the fee is removed from issuance (recycled) instead of being handed to whoever built the block. Alpha-denominated fees are sold and the resulting TAO is recycled the same way.
- **Miner-burn emission scaling is back.** The `(1 − miner_burned)` discount on a subnet's emission share — removed earlier — was restored.
- **The EVM precompile surface grew.** New readers/getters, a root-claim precompile plus getters for unclaimed value, and runtime-constant exposure. A new rule bars root-privileged calls from being implemented in precompiles.
- **Limit orders accept Ledger signatures.** The limit-orders pallet now validates Ledger-style signatures alongside standard formats, and rejects invalid signatures during transaction validation.

## Transaction fees: recycled, not burned, not paid to authors

This is the highest-impact user-facing change, and the wording matters.

> 🚧 **"Burn" is the wrong word here — it's a recycle**
>
> v445 removes the transaction fee from `pallet_subtensor::TotalIssuance` (`TransactionFeeHandler::on_nonzero_unbalanced` does `TotalIssuance.saturating_sub(amount)`). On Bittensor, subtracting from `TotalIssuance` is **[recycling](/docs/recycling)** — the TAO is removed from circulation now and re-enters the emission pool later, pushing the [halving](/docs/#halvinghalvening) further out. It is **not** a permanent [burn](/docs/burning); nothing is destroyed. See the [glossary entry on burn vs recycle](/docs/#burn).

What actually changed:

- **Before:** an earlier runtime routed transaction fees to the **block author** (block builder).
- **v445:** that is reverted. The fee is recycled — the block author receives nothing. The pallet's own test, `tao_transaction_fees_are_recycled`, asserts the block-builder balance is unchanged and that total issuance drops by exactly the fee charged.

Alpha-denominated fees follow the same fate by a different path: the pallet sells the alpha for TAO directly from the subnet account and recycles that TAO (`recycle_tao`), in a single storage transaction so a failed recycle rolls back the alpha withdrawal.

**What this means:** any model that assumed transaction fees accrued to validators/block authors as income is now wrong. Fee revenue does not flow to a participant — it leaves circulation and defers the halving, exactly like registration recycle.

## Emissions: miner-burn scaling restored

v445 restores the **miner-burn emission scaling** in subnet emission shares (PR [#3071](https://github.com/RaoFoundation/subtensor/pull/3071)) after it had been removed. Net effect: the prior behaviour is back — a subnet's demand share is again discounted by `(1 − miner_burned)` before it competes for emission.

This is the same first-stage filter described on the [emission gate](/docs/emission-gate) page: a subnet that burns 100% of its miner emission is zeroed out before the gate even sees it. With the scaling restored, any emission/APY estimate that ignores miner burn will again misplace which subnets actually earn.

See [The emission gate](/docs/emission-gate) and [Price-based emission shares](/docs/price-based-emission-shares) for how this discount feeds into the full emission calculation.

## EVM precompiles: expanded and hardened

The precompile layer (`precompiles/src`) saw a large expansion:

- **New readers and getters** across existing precompiles that were missing them.
- **A root-claim precompile**, plus getters that expose unclaimed value, so EVM contracts can read and act on root-claim state.
- **Runtime-constant exposure** to the EVM, and no-std import fixes.
- **A new invariant:** root-privileged calls must **not** be implemented in precompiles. This is a security boundary, not a feature — it keeps root authority out of the EVM call surface.

The EVM interface artifacts were regenerated to match. See [EVM contracts](/docs/evm-contracts) for how the precompiles fit the wider EVM story.

## Limit orders: Ledger signatures

The limit-orders pallet now supports **Ledger-style signatures** alongside the standard signature formats. Ledger produces human-friendly signatures and signs a hash of the payload when it exceeds 256 bytes; v445 validates these correctly. Invalid signatures are now **rejected during transaction validation** rather than slipping through, and new test vectors cover the added formats.

## Lower-impact fixes

Bundled in the release, less likely to be user-visible but worth noting for anyone indexing chain state:

- **Commitments / storage hygiene** — prevalidate commitment failures ([#3040](https://github.com/RaoFoundation/subtensor/pull/3040)); purge neuron commitments when trimming UIDs and on deregistration ([#3062](https://github.com/RaoFoundation/subtensor/pull/3062)); a storage-bloat reduction migration ([#3061](https://github.com/RaoFoundation/subtensor/pull/3061), [#3076](https://github.com/RaoFoundation/subtensor/pull/3076)). Voting-power state is cleared on subnet dissolution, and `TotalVotingPower` was added to SDK metadata.
- **Proxy / multisig** — preserve intent safety and wrapper order through multisig dispatch, and propagate/refund inner post-dispatch weight for proxy calls ([#3063](https://github.com/RaoFoundation/subtensor/pull/3063)).
- **SDK / generated docs** — refreshed Python SDK metadata, generated transaction links, error pages, and query docs for the new spec.

## Source provenance

- **Release:** [`RaoFoundation/subtensor` v445](https://github.com/RaoFoundation/subtensor/releases/tag/v445). The release body itself is deployment/multisig boilerplate; the changes above are reconstructed from the `v443...v445` commit range and merged PRs, then verified against source at the `v445` tag.
- **On-chain confirmation:** runtime version **445** at block **8,831,003** (2026-08-12 21:06 UTC), Finney, via the Taostats runtime-version index.
- **Transaction fees (verified at `v445`):** `pallets/transaction-fee/src/lib.rs` — `TransactionFeeHandler::on_nonzero_unbalanced` subtracts the fee from `pallet_subtensor::TotalIssuance` (recycle); the alpha path calls `recycle_tao`. Confirmed by the pallet test `tao_transaction_fees_are_recycled` (`pallets/transaction-fee/src/tests/recycling.rs`), which asserts the block author is not paid.
- **Emissions:** miner-burn scaling restored via PR [#3071](https://github.com/RaoFoundation/subtensor/pull/3071).

> 📘 The v445 release train lives on the `RaoFoundation/subtensor` repository (the former `opentensor/subtensor`, now redirected). PR numbers reference that repository.

See also: [Recycling](/docs/recycling) ·
[Burning](/docs/burning) ·
[The emission gate](/docs/emission-gate) ·
[EVM contracts](/docs/evm-contracts)
