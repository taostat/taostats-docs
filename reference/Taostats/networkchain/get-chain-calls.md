---
title: Get Chain Calls
excerpt: >-
  This endpoint lists all extrinsics - as some can be nested inside batch/proxy
  calls.
api:
  file: taostats-1.json
  operationId: get-chain-calls
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## response details

Calls are all of the extrinsics.  Some extrinsics are nested inside proxy or batch extrinsics.  The call endpoint extracts all of the nested extrinsics for easy searching.

```
 {
      "id": "5453552-0012",
      "extrinsic_id": "5453552-0012",
      "parent_id": null,
      "extrinsic_index": 12,
      "success": false,
      "error": {
        "extra_info": "The caller is requesting registering a neuron which already exists in the active set.",
        "name": "HotKeyAlreadyRegisteredInSubNet",
        "pallet": "subtensorModule"
      },
      "pallet": "SubtensorModule",
      "name": "burned_register",
      "full_name": "SubtensorModule.burned_register",
      "args": {
        "hotkey": "0x8878901c0d28e7f5950e1ca56bdeab7a6edea199a83d75dc15b3945aef4e5f26",
        "netuid": 33
      },
      "origin": {
        "__kind": "system",
        "value": {
          "__kind": "Signed",
          "value": "0xca35b13b673721f9f7d6720602b5f8630fa0fed267177f1d0bf5b58f1681fd2d"
        }
      },
      "origin_address": "0xca35b13b673721f9f7d6720602b5f8630fa0fed267177f1d0bf5b58f1681fd2d",
      "timestamp": "2025-04-28T23:04:00Z",
      "block_number": 5453552
    },
```
