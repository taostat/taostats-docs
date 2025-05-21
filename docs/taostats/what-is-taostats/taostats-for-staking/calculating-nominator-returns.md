---
title: Calculating Nominator returns
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
# Key Concepts

## Bittensor Day

A "Bittensor day" consists of 7,200 blocks. While the actual time may fluctuate slightly, this measurement is used because hotkeys are drained every 7,201 blocks.

## Non-Viable Stake

Stake added during a hotkey epoch is considered "non-viable" and ineligible for nominator rewards during that epoch. This prevents system abuse where nominators might add stake just before drainage to receive higher rewards.

<br />

# Calculation Process

## Required Measurements

`stake_before_reward`: Nominator's stake on the block before validator's hotkey drainage  
`non_viable_stake`: Nominator's non-viable stake on the block before validator's hotkey drainage  
`stake_after_reward`: Nominator's stake on the block of validator's hotkey drainage  
**Important**: Verify no stake/unstake actions occurred on this block

## Formula

```javascript
viable_stake = stake_before_reward - non_viable_stake
profit = stake_after_reward - stake_before_reward
multiplier = 1000 / viable_stake
nominator_return_per_1000_tao_per_day = profit * multiplier
apr = nominator_return_per_1000_tao_per_day * 365
```

> 📘 The Law of Big Numbers (AKA the Whale Effect)
> 
> Nominator returns can increase significantly when a whale (large stakeholder) joins a validator. This occurs because:
> 
> 1. Non-viable stake is still considered viable by subnets during their epochs
> 2. Subnets continue to drain pending emissions to hotkeys
> 3. When a whale stakes on a validator with little existing stake, their contribution generates rewards that are shared among:
>    - The validator
>    - Existing nominators
> 
> This creates an opportunity for smaller stakeholders ("prawns") to receive unexpectedly high returns if they're positioned on a validator that attracts a whale investor.