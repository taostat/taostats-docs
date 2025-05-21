---
title: Get Staking/Delegation Events
excerpt: ''
api:
  file: taostats-1.json
  operationId: get-stakingdelegation-balances
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
      "id": "finney-68-0x828e7eabc592c6d03c62ab0799cda1c0de0b8f57fb7d542deba479957a9dc573-0x96f0651155c3a50c68d6fbe4175f512627d6517140ce00ae495e8b4a81050815-5453624-140",
      "block_number": 5453624,
      "timestamp": "2025-04-28T23:18:24.001Z",
      "action": "DELEGATE", direction delegate or undelegate
      "nominator": {
        "ss58": "5FUcTAuTxS5iS7FyP3CwHee53m3mtYYTVS9hJukfZF5hC8KU",
        "hex": "0x96f0651155c3a50c68d6fbe4175f512627d6517140ce00ae495e8b4a81050815"
      },
      "delegate": {
        "ss58": "5F1tQr8K2VfBr2pG5MpAQf62n5xSAsjuCZheQUy82csaPavg",
        "hex": "0x828e7eabc592c6d03c62ab0799cda1c0de0b8f57fb7d542deba479957a9dc573"
      },
      "amount": "7092857", tao as rao
      "alpha": "135443860", alpha as rao
      "usd": "2.70", value in USD
      "alpha_price_in_tao": "0.05236750488357316456",
      "alpha_price_in_usd": "19.94",
      "netuid": 68,
      "extrinsic_id": "5453624-0032",
      "is_transfer": null,
      "transfer_address": null
    },
```