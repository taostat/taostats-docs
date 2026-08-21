---
title: Tokenomics
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

Learn how tao and alpha tokens are emitted and distributed to participants on Bittensor.

> 📘 The one-line version: `tao` has a fixed **21M** supply on a Bitcoin-style
>   halving schedule. Each subnet also issues its own `alpha` token — and every
>   alpha token has the **same 21M max supply** on its own halving schedule. Each
>   subnet's alpha trades against tao at its own exchange rate, set by that
>   subnet's liquidity pool.

## Supply

> 📘 The figures below are an illustrative snapshot, **not live**. For the current numbers, see the [Taostats tokenomics page](https://taostats.io/tokenomics/) or query the API.

| Metric | Value |
| --- | --- |
| Total supply | `21,000,000` τ |
| Circulating supply | `~11.2M` τ (snapshot) |
| In circulation | `~53%` (snapshot) |

The total issuance shown on Taostats is taken directly from the substrate
blockchain and updates automatically. Because tao used to recycle registrations
is burned back into the unissued supply, the halvening schedule lengthens over
time — this is calculated at the current block/issuance.

## Halving

Bittensor tokens follow the Bitcoin halving schedule. The **total token
issuance**, not the block number, determines the exact point each halvening
occurs (see [Halving](/docs/halving)).

Because the halvening is issuance-driven, you read it off the chain rather than
counting blocks. The current block and issuance are available from the API, for
example:

```bash
curl -H "Authorization: $TAOSTATS_API_KEY" \
  "https://api.taostats.io/api/block/v1?limit=1"
```

## Emission split

Alpha emission is divided between the participants and the subnet pool:

- **Miners** earn incentive for useful work
- **Validators** earn dividends for accurate consensus
- **Stakers** earn a share of the validator's dividends

See [Staking in dTao](/docs/staking-in-dtao) for how to participate.

## In this section

- [Tokenomics](/docs/tokenomics)
- [TAO](/docs/tao)
- [Alpha tokens](/docs/alpha-tokens)
- [Alpha emission](/docs/alpha-emission) — *see How emission works*
- [Halving](/docs/halving)
- [Burning](/docs/burning)
- [Recycling](/docs/recycling)
- [Price Impact and Slippage](/docs/slippage)
