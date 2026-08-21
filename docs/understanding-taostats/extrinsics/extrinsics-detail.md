---
title: Extrinsic Information
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

The extrinsics detail page describes what happened in the extrinsic.

The top section of each extrinsic page gives a general breakdown of the extrinsic (this is data that is present in each extrinsic)

<Image border={false} alt="Taostats extrinsic detail page top section showing hash, status, block, timestamp, account, name, and fee fields" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/eeb860cf6dfbbd16.png" />

* **Hash**: The hash on chain describing the extrinsic
* **Status** : Did it work or not?
* **Block**: The block where the extrinsic occurred.
* **Timestamp**: When the block was issued
* **Account**: the coldkey that called the eextrinsic
* **Name**: The extrinsic called
* **Extrinsic Fee**: Some extrinsics have a on-chain fee.

# Extrinsic Parameters

<Image border={false} alt="Taostats extrinsic parameters panel with parsed and raw tabs listing named parameter label-value pairs" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/ccce8edb65a35f45.png" />

Depending on the extrinsic called, these parameters may vary.  This extrinsic shows a transfer of alpha to a different hotkey on Subnet 13.

# Events

Extrinsics are carried out through chain events.  This table lists all of the events tied to the Extrinsic:

<Image border={false} alt="Taostats extrinsic detail events table with event ID, name, pallet, phase, extrinsic ID, and time columns" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/0a4540f563e40365.png" />

* **Event ID**: Unique Identified for the event on chain
* **Name**: Event Name
* **Pallet**: Type of event called
* **phase**: Phase of the event
* **Extrinsic**: Extrinsic related to the event
* **Time**: When the Events were called.
