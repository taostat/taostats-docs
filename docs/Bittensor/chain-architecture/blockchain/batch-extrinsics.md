---
title: Batch Extrinsics
excerpt: Batch extrinsics allow many calls to be made in a single extrinsic.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Batch extrinsics do what you expect - they batch many extrinsics, so that they occur on the same block.  In Bittensor, there are three extrinsics for batching calls:

* Utility.batch
* Utility.batch\_all
* Utility.force\_batch

<br />

The differences:

If an extrinsic in `Utility.batch` pr `Utility.batch_all` fails, all of the extrinsics fail.  `Utility.force_batch`will execute all extrinsics, and ignore failures.

<br />

<br />

Batch extrinsics are not free, and a fee will be assessed based on the calls inside.