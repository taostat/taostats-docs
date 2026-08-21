---
title: MEVbots explained
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

why do we need mev shield, and how does it work?

Maximum Extractable Value (MEV) bots scan the chain and look for transactions to "steal" assets from.  There have been a number of approaches to hinder these Bots from operating on chain.

When a transaction moves through a liquidity pool, there is an opportunity for slippage: where another transaction precedes your transaction, changing the price and affecting the amount of tao/alpha you receive.

> 📘 Example
>
>   An isolated transaction will have a small price impact due to the liquidity pool
>
>   <Image border={false} alt="Diagram of a single token swap through an AMM subnet pool, with input tau, pool tau/alpha reserves, output alpha, and a resulting price-impact percentage" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/80fd04a5e81273fc.png" />
>
>   But a large transaction in front of this one adds slippage:
>
>   <Image border={false} alt="Diagram decomposing an AMM swap's adverse execution into price impact plus slippage caused by a large front-running transaction" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/c9202b8d3926c0ce.png" />
>
>   In this example, 4% of the transaction is lost to slippage.
>
>   This is what the MEV bots do.

# First fix: Limits

All transactions should set a slippage limit.  This means - "hey, the price is x, and I am ok with a change of y% for the transaction."

The slippage limit should be small - a 4% slippage limit in the example above cost 20 alpha (\~ 2 tao).  For high liquidity subnets, you can be well below 1%.

## The MEV bots calculate their MAX extraction on every transaction

f your limit is very loose - the bot may decide to attack your transaction.

If you have no limit set:  The MEV bots can extract as much as they want.

<Image border={false} alt="Dark-themed transaction log table with buy/sell pills, entity, alpha amount, tao value, per-unit price, percentage, and truncated wallet address columns" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/3aa8467f253c9b52.png" />

# MEVShield

While a tight limit price on your transfer should be enough to stop MevBots,  the chain has also launched MevShield.

Currently in version 1.0:  Mevshield encrypts your transfer, so that the MEVbot cannot read the details.  ON the next block, your transaction is decrypted and processed.

## Advantages:

By encrypting the transaction, the MEVBot cannot see what you have done, and therefore cannot schedule a transaction in front of your trade.

## Disadvantages

Each transaction using MEVShield must be signed twice:

* Sign the transaction
* sign the encryption wrapper.

Taostats (and other providers) now offers the ability to sign the encryption wrapper to save double password entry.

<Image border={false} alt="Transaction confirmation panel with two checkboxes for enabling MEV shield protection and delegating submission, plus a Confirm button" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/41306087b09bd93b.png" />

MevShield 2.0 is in development with more enhancements.

## Why does Taostats disable MevShield for transactions  `<1` tao?

For transactions `<1` tao, you are not likely going to be mevved - the potential gain for the attackers is too small compared to the risk.

## Why does taostats disable MevShield for root stakes?

Root staking has no price impact or slippage you cannot be mevved on a root transaction - so no need for 2 signatures.
