---
title: Block Details
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

The section of taostats dedicated to stats of the blockchain.

A chart showing the 10 most recent blocks emitted from the Bittensor blockchain:

<Image border={false} alt="Taostats chain explorer blocks table listing recent blocks with height, spec version, hash, events count, extrinsics count, and time columns" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/4f8de2e630c2dff0.png" />

Each block has a:

* Spec number: the specification of Bittensor that generated the block
* Events: All of the events emitted by extrinsics in the block.
* Extrinsics: Transactions submitted to the chain. Each extrinsic can emit one or more events when it executes.
* Time since emitted: The age of the block.

Clicking on the block leads to details on the block:

<Image border={false} alt="Taostats block details page showing label-value fields for timestamp, block time, block height, hash, parent hash, and spec version" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/d5c220be7a03fc1a.png" />

# Extrinsics:

An extrinsic is a transaction submitted to the chain; each extrinsic emits one or more events when it executes, and a block contains many extrinsics. In the table for each block, the Extrinsic Name, the signing account (coldkey) and the result (succeeded/failed) are displayed:

<Image border={false} alt="Taostats block extrinsics table with ID, name, account, and result status columns, plus a rows-per-page selector" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/202c236e8d1a2bf5.png" />

# Events: emitted by extrinsics

An extrinsic emits one or more events when it executes. A block contains many extrinsics, and each extrinsic can emit multiple events. All of the events are displayed in the Event table. They are tied to Event names and the Extrinsic that is the parent of a group of events.

> 📘 **The initial events in each block are System events (block initialization, etc.) and are not displayed.**
>
> They can still be viewed by opening another Event, and changing the URL value.

<Image border={false} alt="Taostats block events table listing events emitted by extrinsics with ID, name badge, and originating extrinsic columns" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/5e66bec85d57bf0b.png" />
