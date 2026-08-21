---
title: How emission works
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

Every block the chain emits TAO, mints alpha in each subnet, and distributes it down to individual stakeholders. This section follows that flow **step by step** — each page picks up where the previous one left off, with a *How we got here* and a *What's next* at the top and bottom.

## The flow, step by step

1. **[TAO emission](/docs/tao-emission)** — 0.5 τ/block is split across subnets; each subnet's share is injected into its pool or spent as a chain buy.
2. **[Alpha emission](/docs/alpha-emission)** — each subnet mints alpha per block, split into `alpha_in` (pool) and `alpha_out` (1 α to participants).
3. **[Split `alpha_out` among participants](/docs/split-alpha-out)** — owner 18%, miners 41%, validators 41%.
4. **[Parent / child hotkeys](/docs/emission-parent-hotkeys)** — aggregate each validator's dividends across its parent and child hotkeys.
5. **[Root vs alpha split](/docs/stakeholder-emissions-root-vs-alpha)** — divide the validator's dividends into a root proportion and an alpha proportion.
6. Distribute to stakeholders — **[root](/docs/stakeholder-emissions-root)** and **[alpha](/docs/stakeholder-emissions-alpha)**.

## Pages in this section
