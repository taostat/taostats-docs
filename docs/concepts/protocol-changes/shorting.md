---
title: Shorting (PR #2764) — Fixed-Liability Covered Continuous-Unwind Model
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

> 📘 **Status:** pending · **Last reviewed:** 2026-06-27 · [Source PR](https://github.com/opentensor/subtensor/pull/2764)

> 🚧 **Not live on mainnet**
>
> This page describes Subtensor PR #2764, the v3.6.1 **Fixed-Liability Covered
> Continuous-Unwind Model** for shorting alpha tokens. The runtime flag
> `ShortsEnabled` defaults to `false` and the feature is gated behind the
> trading-games activation. Do not make production decisions assuming shorts
> are available on mainnet. When the flag flips, this section will be
> re-reviewed and cross-cut into tokenomics, staking, and chain pages.

## What covered shorting is

A **covered short** on Bittensor is a leveraged bearish bet on a subnet's
alpha token. You fund a TAO floor `P` (your max loss), borrow a fixed
quantity of alpha `Q` from the subnet pool at today's price, and profit if
alpha depreciates. To close, you buy `Q` back from the pool — if the price
fell, the buyback costs less than your retained buffer `R` and you keep the
difference. If the price rose, the buyback eats into `R` and then into `P`.

Crucially, there is **no margin liquidation**. There is no liquidation price
to target, no short squeeze, no MEV-driven forced close. Default happens
only on time — when the retained buffer decays to a dust threshold — or on
subnet deregistration. Your maximum loss is capped at the floor `P` you
funded at open.

The model matters for subnet economics because it injects discipline
without leaving TAO stranded. Every τ removed from the pool at open is
returned: via daily decay (`R` and `E` drift back into reserves over the
position's life), via the close settlement, or — if the trader abandons —
via recycling `P` into the TAO emission pool as `tao_in`. There is no path
that permanently drains pool reserves.

## Pages in this section

- [Explainer](/docs/shorting-explainer) — conceptual
  walkthrough: the letter glossary, opening a short, daily decay, the three
  close scenarios, how you lose, and why subnets benefit from this model.
- [Flow — ledger story](/docs/flow) — the same
  short followed in three parts (open / decay / three closes) with full
  TAO/α/Price/P/E/R/Q ledger tables and the close-decision rule at the end.
- [Technical reference](/docs/technical) —
  spec-to-Subtensor notation map, closed-form open math, per-block decay
  pseudocode, the three close paths, storage layout (`ShortPosition` and
  `ShortAgg` Rust structs), governance parameters, the four extrinsics
  (call indices 139–142), reserve accounting model, and terminal
  deregistration settlement.
- [Simulator](/docs/sim) —
  interactive simulator for opens, closes, and decay trajectories.
  Loads Chart.js from a CDN; otherwise self-contained.

## Source

These pages are the canonical migration of Rufus's HTML explainers,
authored against the PR #2764 specification (`DESIGN.md` §1–17 and
`IMPLEMENTATION_PLAN.md`). Where wording works, it has been preserved
lock, stock, and barrel.
