---
title: Extrinsics Detail
excerpt: The extrinsics detail page describes what happened in the extrinsic.
deprecated: false
hidden: false
metadata:
  robots: index
---
# Extrinsic Information

The top section of each extrinsic page gives a general breakdown of the extrinsic (this is data that is present in each extrinsic)

![](https://files.readme.io/75288b7100c10ab7b1f00e660d84b716a362a7258fc0bd0ff095cd39060c2f17-image.png)

<br />

* **Hash**: The hash on chain describing the extrinsic
* **Status** : Did it work or not?
* **Block**: The block where the extrinsic occurred.
* **Timestamp**: When the block was issued
* **Account**: the coldkey that called the eextrinsic
* **Name**: The extrinsic called
* **Extrinsic Fee**: Some extrinsics have a on-chain fee.

<br />

# Extrinsic Parameters

![](https://files.readme.io/7adae9ecb6eb5df68e0d88686b8181707e837ae4a81664c7f328a1c6f8e3aa0e-image.png)

Depending on the extrinsic called, these parameters may vary.  This extrinsic shows a transfer of alpha to a different hotkey on Subnet 13.

<br />

# Events

Extrinsics are carried out through chain events.  This table lists all of the events tied to the Extrinsic:

<br />

![](https://files.readme.io/069983bf4abcadef9c833c66f4b5af0d6040e68795d372c6dc698cbf57f3f08f-image.png)

* **Event ID**: Unique Identified for the event on chain
* **Name**: Event Name
* **Pallet**: Type of event called
* **phase**: Phase of the event
* **Extrinsic**: Extrinsic related to the event
* **Time**: When the Events were called.