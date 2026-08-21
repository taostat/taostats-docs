---
title: Taostats governance
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

Taostats Governance lets the Bittensor community raise proposals and vote with weight drawn from real on-chain holdings — with no gas, no fees, and nothing written on-chain. It is available at [governance.taostats.io](https://governance.taostats.io/how-it-works).

> 📘 **Completely free, completely off-chain.** Voting and raising proposals cost nothing. You sign a one-time message to prove you own your coldkey, but never an on-chain transaction — no gas, no funds move. Governance here is an off-chain signal, weighted by your verified on-chain balances.

## How it works

1. **Sign in.** Sign in with Taostats and sign a one-time message to prove you own your coldkey. This is off-chain — no transaction, no gas, nothing moves.
2. **Pick an option.** Open a proposal, choose your option, and cast your vote. One vote per coldkey.
3. **Weighted by holdings.** Your weight is read from your on-chain balances. Subnet polls use your 30-day average alpha in that subnet; root polls use your 30-day average TAO-equivalent across all holdings.
4. **Frozen & fair.** Your weight is locked in at your first vote. You can change your option (once per epoch), but the weight stays fixed. Averaging over 30 days stops last-minute stake-loading from buying votes.

## The details

- **One vote per coldkey.** Multiple hotkeys under one coldkey still count as a single vote, weighted by the coldkey's aggregate holdings.
- **Who can propose.** Anyone holding at least 1 TAO-equivalent in a poll's scope can raise a proposal in it.
- **Conviction weighting (optional).** A proposal can count locked (convicted) alpha more heavily, or restrict eligibility to convicted alpha only. Every poll shows its exact rule under *"How this poll is weighted."*
- **Transparent.** Every vote, its weight, and the full audit log are public. Shared links never include your coldkey or hotkey.

## Poll scopes

| Scope | Voting weight |
| --- | --- |
| **Subnet poll** | Your 30-day average alpha in that subnet |
| **Root poll** | Your 30-day average TAO-equivalent across all holdings |

> 📘 **Why the 30-day average?** Reading a rolling 30-day balance rather than a live snapshot prevents anyone from loading stake immediately before a vote to inflate their weight, then unwinding it afterwards. Governance weight reflects sustained holdings, not a momentary position.

## Get started

Head to [governance.taostats.io](https://governance.taostats.io/how-it-works), sign in with Taostats, and cast your first vote — no wallet transaction required.
