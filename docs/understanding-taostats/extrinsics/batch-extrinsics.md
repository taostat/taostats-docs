---
title: Extrinsics: batch
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

Batch extrinsics allow many calls to be made in a single extrinsic.

Batch extrinsics do what you expect - they are a compilation of  many extrinsics, allowing the user to submit many transactions simultaneously. In Bittensor, there are three extrinsics for batching calls:

* Utility.batch
* Utility.batch\_all
* Utility.force\_batch

The differences:

If an extrinsic in `Utility.batch` pr `Utility.batch_all` fails, all of the extrinsics fail.  `Utility.force_batch`will execute all extrinsics, and ignore failures.

Batch extrinsics are not free, and a fee will be assessed based on the calls inside.
