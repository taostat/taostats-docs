---
title: Get Extrinsics
excerpt: >-
  Lists all primary extrinsics. To get extrinsics in batch/proxy calls use he
  Get Calls endpoint
api:
  file: taostats-2.json
  operationId: get-extrinsics
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

```
    {
      "timestamp": "2025-04-28T22:59:00.001Z",
      "block_number": 5453527,
      "hash": "0xc7a314f07c868be15ba745d4a3679c597e839e0824b796d2e60e95fbf1594c53",
      "id": "5453527-0020",
      "index": 20, extrinsic index
      "version": 4,
      "signature": {
        "address": {
          "__kind": "Id",
          "value": "0x96f0651155c3a50c68d6fbe4175f512627d6517140ce00ae495e8b4a81050815"
        },
        "signature": {
          "__kind": "Sr25519",
          "value": "0xa699fff74ebc9d5f4bf9f0c4a9bb90b8ee0dab5920109121c80e61130c618f1b8e16790966a831df593d1b0dc736ed4b81b7bac83620a6829cb8974ce2a8e78c"
        },
        "signedExtensions": {
          "chargeTransactionPayment": "0",
          "checkMetadataHash": {
            "mode": {
              "__kind": "Disabled"
            }
          },
          "checkMortality": {
            "__kind": "Immortal"
          },
          "checkNonce": 2912
        }
      },
      "signer_address": "0x96f0651155c3a50c68d6fbe4175f512627d6517140ce00ae495e8b4a81050815",
      "tip": "0",
      "fee": "0",
      "success": true,
      "error": null,
      "call_id": "5453527-0020",call Id
      "full_name": "SubtensorModule.add_stake",
      "call_args": {
        "amountStaked": "7142857", amount staked in rao
        "hotkey": "0x828e7eabc592c6d03c62ab0799cda1c0de0b8f57fb7d542deba479957a9dc573",validator hotkey
        "netuid": 68
      }
    },
```