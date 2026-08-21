---
title: Price-based emission shares (PRs #2779 + #2781)
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

> 🚧 **Superseded as the final formula by spec 440**
>
> As of **spec 440** (2026-07-27), the price-based quantity on this page —
> `price × (1 − miner_burned)`, renormalized — is now the **demand input** to a new
> [emission gate](/docs/emission-gate), *not* the final
> emission share. Emission is no longer proportional to demand. This page still
> explains how demand is built; see **[The emission gate (spec 440)](/docs/emission-gate)**
> for what happens to it next.

> 📘 **Now live on chain**
>
> Price-based emission shares are **live on chain** (Subtensor PRs
> [#2779](https://github.com/opentensor/subtensor/pull/2779),
> [#2781](https://github.com/opentensor/subtensor/pull/2781), and
> [#2800](https://github.com/opentensor/subtensor/pull/2800)). The full
> explainer has moved into the emission concept docs.

For how emission works now — the live per-block share formula
(`share_i ∝ price_i × (1 − miner_burned_i)`), the miner-burn scaling, the
alpha-injection cap, and worked examples — see:

**[Tao Emission](/docs/tao-emission)** in Concepts → Tokenomics → How emission works.
