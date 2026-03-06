---
title: Sentiment
deprecated: false
hidden: false
metadata:
  robots: index
---
# Subnet Sentiment Index (SSI)

The Subnet Sentiment Index is a composite score (0–100) that measures market sentiment for each subnet on the Bittensor network. It replaces the previous Fear & Greed Index with a more nuanced, multi-factor approach.

## How It Works

The SSI combines seven components, each capturing a different dimension of market sentiment. All components are scored 0–100 using sigmoid smoothing, then combined with fixed weights:

```
SSI = (0.25 × Buy/Sell Pressure)
    + (0.20 × Price Momentum)
    + (0.15 × Volume Trend)
    + (0.15 × Tao Flow)
    + (0.10 × Emissions Yield)
    + (0.10 × Rank Momentum)
    + (0.05 × Participation Breadth)
```

## Components

### 1. Buy/Sell Pressure — 25%

Measures directional conviction by combining two ratios:

* **Volume ratio** (60% weight): Buy volume ÷ total volume over the last 24 hours. A ratio above 0.5 means more TAO is flowing into buy-side trades.
* **Participant ratio** (40% weight): Unique buyers ÷ total unique participants over 24 hours. This prevents a single large trade from skewing the score — broad-based buying is a stronger signal than one whale.

The blended ratio is mapped through a sigmoid function centered at 0.5.

**Interpretation:**

* High score → majority of volume and participants are buying
* Low score → selling dominates
* Near 50 → balanced market

### 2. Price Momentum — 20%

A weighted blend of price changes across four timeframes:

| Timeframe | Weight |
| --------- | ------ |
| 1 hour    | 10%    |
| 1 day     | 30%    |
| 1 week    | 40%    |
| 1 month   | 20%    |

The weekly timeframe carries the most weight to capture meaningful trends while filtering out hourly noise. A +5% daily move means something different in the context of a -20% weekly decline versus a +30% weekly rally.

The blended momentum value is passed through a sigmoid function centered at 0 with a scale of 0.08.

### 3. Volume Trend — 15%

Compares current 24-hour volume against the 7-day average, then adjusts for price direction:

| Volume        | Price   | Interpretation                     |
| ------------- | ------- | ---------------------------------- |
| Above average | Rising  | Conviction buying — greed signal   |
| Above average | Falling | Capitulation — fear signal         |
| Below average | Rising  | Quiet accumulation — mild positive |
| Below average | Falling | Apathy/drift — mild fear           |

This matters because rising volume isn't inherently bullish or bearish — it's a measure of conviction. The price direction reveals _which_ conviction.

### 4. Tao Flow — 15%

Tracks capital movement through two lenses:

* **Staked ratio** (60% weight): Alpha tokens staked vs. tokens in the pool. A higher staked ratio means holders are locking tokens up rather than keeping them liquid to sell — a conviction signal.
* **Liquidity trend** (40% weight): Change in pool liquidity over 7 days. Growing liquidity indicates capital inflow; shrinking liquidity signals outflow.

This is often considered the "smart money" signal. Price can be moved short-term by a single large trade, but capital flow patterns across a week are harder to fake.

### 5. Emissions Yield — 10%

Evaluates validator yield attractiveness, adjusted for market context:

* Base score from the stake-weighted average APY of the top 10 validators
* **Price trend modifier**: High yield with a rising price = genuine demand (full score). High yield with a falling price = potential "farm and dump" pattern (discounted score).
* Epoch participation health as a secondary factor

This component catches a common pattern: subnets where validators earn strong rewards but immediately sell, creating downward price pressure despite seemingly attractive yields.

### 6. Rank Momentum — 10%

Captures a subnet's position relative to the broader ecosystem:

* **Rank change** (40% weight): Movement in subnet ranking over 7 days. A ±3 rank shift is considered significant.
* **Market cap change** (60% weight): Daily market capitalisation change as a percentage.

A subnet improving its rank means it's gaining market share relative to all other subnets — not just going up in isolation.

### 7. Participation Breadth — 5%

A quality modifier that measures how distributed trading activity is:

* **Diversity**: Trades per unique participant — lower is better (more individual decision-makers rather than a few accounts trading repeatedly)
* **Market thickness**: Total unique participants, where higher counts indicate healthier markets

Thin markets with few participants have their score pulled toward neutral/fear, reflecting the inherent uncertainty of low-activity subnets.

## Sigmoid Smoothing

... (35 lines left)

ssi-docs-page.md
7 KB
Here is the required tweets for Taostats. Option A will be the initial tweet that Taostats will use... Option B will be one that I will use to quote Taostats' tweet... Option C can be an article which I need to post here that we will follow up with.

# SSI Twitter Thread — Draft

## Option A: Thread (5 tweets)

### 1/5

We just shipped a completely new sentiment engine for every subnet on Taostats.

ssi-twitter-thread.md
3 KB
﻿

# Subnet Sentiment Index (SSI)

The Subnet Sentiment Index is a composite score (0–100) that measures market sentiment for each subnet on the Bittensor network. It replaces the previous Fear & Greed Index with a more nuanced, multi-factor approach.

## How It Works

The SSI combines seven components, each capturing a different dimension of market sentiment. All components are scored 0–100 using sigmoid smoothing, then combined with fixed weights:

```
SSI = (0.25 × Buy/Sell Pressure)
    + (0.20 × Price Momentum)
    + (0.15 × Volume Trend)
    + (0.15 × Tao Flow)
    + (0.10 × Emissions Yield)
    + (0.10 × Rank Momentum)
    + (0.05 × Participation Breadth)
```

## Components

### 1. Buy/Sell Pressure — 25%

Measures directional conviction by combining two ratios:

* **Volume ratio** (60% weight): Buy volume ÷ total volume over the last 24 hours. A ratio above 0.5 means more TAO is flowing into buy-side trades.
* **Participant ratio** (40% weight): Unique buyers ÷ total unique participants over 24 hours. This prevents a single large trade from skewing the score — broad-based buying is a stronger signal than one whale.

The blended ratio is mapped through a sigmoid function centered at 0.5.

**Interpretation:**

* High score → majority of volume and participants are buying
* Low score → selling dominates
* Near 50 → balanced market

### 2. Price Momentum — 20%

A weighted blend of price changes across four timeframes:

| Timeframe | Weight |
| --------- | ------ |
| 1 hour    | 10%    |
| 1 day     | 30%    |
| 1 week    | 40%    |
| 1 month   | 20%    |

The weekly timeframe carries the most weight to capture meaningful trends while filtering out hourly noise. A +5% daily move means something different in the context of a -20% weekly decline versus a +30% weekly rally.

The blended momentum value is passed through a sigmoid function centered at 0 with a scale of 0.08.

### 3. Volume Trend — 15%

Compares current 24-hour volume against the 7-day average, then adjusts for price direction:

| Volume        | Price   | Interpretation                     |
| ------------- | ------- | ---------------------------------- |
| Above average | Rising  | Conviction buying — greed signal   |
| Above average | Falling | Capitulation — fear signal         |
| Below average | Rising  | Quiet accumulation — mild positive |
| Below average | Falling | Apathy/drift — mild fear           |

This matters because rising volume isn't inherently bullish or bearish — it's a measure of conviction. The price direction reveals _which_ conviction.

### 4. Tao Flow — 15%

Tracks capital movement through two lenses:

* **Staked ratio** (60% weight): Alpha tokens staked vs. tokens in the pool. A higher staked ratio means holders are locking tokens up rather than keeping them liquid to sell — a conviction signal.
* **Liquidity trend** (40% weight): Change in pool liquidity over 7 days. Growing liquidity indicates capital inflow; shrinking liquidity signals outflow.

This is often considered the "smart money" signal. Price can be moved short-term by a single large trade, but capital flow patterns across a week are harder to fake.

### 5. Emissions Yield — 10%

Evaluates validator yield attractiveness, adjusted for market context:

* Base score from the stake-weighted average APY of the top 10 validators
* **Price trend modifier**: High yield with a rising price = genuine demand (full score). High yield with a falling price = potential "farm and dump" pattern (discounted score).
* Epoch participation health as a secondary factor

This component catches a common pattern: subnets where validators earn strong rewards but immediately sell, creating downward price pressure despite seemingly attractive yields.

### 6. Rank Momentum — 10%

Captures a subnet's position relative to the broader ecosystem:

* **Rank change** (40% weight): Movement in subnet ranking over 7 days. A ±3 rank shift is considered significant.
* **Market cap change** (60% weight): Daily market capitalisation change as a percentage.

A subnet improving its rank means it's gaining market share relative to all other subnets — not just going up in isolation.

### 7. Participation Breadth — 5%

A quality modifier that measures how distributed trading activity is:

* **Diversity**: Trades per unique participant — lower is better (more individual decision-makers rather than a few accounts trading repeatedly)
* **Market thickness**: Total unique participants, where higher counts indicate healthier markets

Thin markets with few participants have their score pulled toward neutral/fear, reflecting the inherent uncertainty of low-activity subnets.

## Sigmoid Smoothing

Every component uses a sigmoid function rather than linear scaling:

```
score = 100 / (1 + e^(-(value - center) / scale))
```

This provides:

* **Smooth, bounded output** — no hard clipping at 0 or 100
* **Diminishing sensitivity at extremes** — a single outlier metric can't dominate the overall score
* **Symmetry around neutral** — equal sensitivity to fear and greed signals

## Data Sources

Each subnet's SSI is calculated from three data points:

| Data                    | Source              | Used For                                                       |
| ----------------------- | ------------------- | -------------------------------------------------------------- |
| Current subnet snapshot | Subnet Pool API     | Price, volume, buy/sell stats, rank, liquidity, staking ratios |
| 7-day historical data   | Pool History API    | Volume averages, liquidity trends, rank changes                |
| Validator performance   | Validator Yield API | APY calculations, epoch participation                          |

## Interpreting SSI

The SSI is designed to differentiate between subnets. A subnet in "Greed" territory (61–80) has genuinely strong multi-factor momentum — it's not just one metric pulling it up.

Some patterns to look for:

* **High SSI + high volume**: Strong consensus bullish sentiment
* **High SSI + low volume**: Quiet accumulation, potentially fragile
* **Low SSI + high volume**: Active selling/capitulation — could signal a bottom or continued decline
* **SSI divergence from price**: If SSI is declining while price holds, underlying fundamentals may be weakening

The SSI updates with each data refresh and is available on every subnet page on Taostats.
