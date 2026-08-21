---
title: Subnet Registration
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

Subnet registration and deregistration are live on the chain.

Anyone can register a new subnet by paying the current registration (lock) cost in TAO. The cost is demand-based: it rises as registrations become more frequent and decays back down over time.

## Current registration cost

Read the current lock cost with the [Bittensor CLI](/docs/command-line-tool):

```
btcli subnet lock_cost
>> Subnet lock cost: τ3,796.780457067
```

The live and historical cost is also available programmatically:

* [Get Subnet Registration Cost (latest)](/api-reference/subnet/get-subnet-registration-cost-latest)
* [Get Subnet Registration Cost (history)](/api-reference/subnet/get-subnet-registration-cost-history)

Or view the historical chart on the [Subnet Home](https://taostats.io/subnets).

## Where the cost goes

A portion of the registration cost is paid into the subnet's liquidity pool (with a matching amount of alpha minted to hold the price); the remainder is recycled.

The registering owner does *not* receive a matching alpha allocation. The earlier "alpha-to-owner" mechanic — where the subnet owner was minted alpha equal to the lock cost at registration — has been removed. Owners now participate in their subnet's economics through the dTao market like any other holder.

## Registration cadence and cap

Once a subnet is registered, there is a 4-day window before the next registration can occur.

If the current maximum number of subnets has been reached, registering a new subnet deregisters the lowest-priced subnet (subject to immunity — see below).

## Immunity

New subnets have 4 months of immunity from deregistration.

## Deregistration

For how a subnet is chosen for deregistration and how alpha holders are paid out, see [Subnet Deregistration](/docs/subnet-deregistration).
