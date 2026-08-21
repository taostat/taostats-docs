---
title: Tao Emission
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

The token of the Bittensor network

In Asian philosophy, Tao is the natural way of the universe, an unexplainable force that is an important part of everyday life. It gets its name from the Chinese character which means “the way” or “the path”.  If you are a Star Wars fan - think "The Force."

The tao token similarly pervades into every part of the Bittensor ecosystem.  Tao is the token that is foundational to all of the tokens earned by core participants of the Bittensor network.

For a high-level overview, the [Tokenomics](https://taostats.io/tokenomics/) page has a great history and background of the tao token.

One block is written to the Bittensor blockchain approximately every 12 seconds.

For every block written, 0.5 tao is created (in the current halving cycle — the first halving occurred in December 2025). (see [Tao Emission Distribution](/docs/tao-emission) for details)

This means a maximum of 3600 tao are created every day. If a block takes longer to be produced, this can lower the daily emitted blocks.

You can visualise the chain block production at [taostats](https://taostats.io/analytics/blocks)

<Image border={false} alt="Analytics area chart titled chain block production, plotting block count per period over time with granularity, date, and CSV export controls" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/4928d5bb6ace5c4a.png" />

## Distribution of Emitted tao

Each block's emitted tao is distributed across the subnet pools according to each subnet's emission share. The exact formula lives in one canonical place — see **[Tao Emission](/docs/tao-emission)** for the full mechanic and **[Price-based subnet emission shares](/docs/price-based-emission-shares)** for how each subnet's share is computed.

A subnet's emission % is simply its share of the per-block tao emission.

## Recycling

Recycled tao is tao that is removed from circulation back into the unissued supply.

[Recycling](/docs/recycling)

## Burned

Tao can be burned, this is tao that is no longer in circulation, and is no longer accessible.

## tao vs. rao

1 billionth of a tao is a rao.  10^9 rao = 1 tao. The Bittensor network has a hard limit of 21,000,000 (21 million) tao.

## Halving

Bittensor follows the halving schedule of Bitcoin. The first halving occurred in December 2025 when 10.5M tao had been emitted; block emission dropped from 1 tao to 0.5 tao per block at that point.

[Halving](/docs/halving)
