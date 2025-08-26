---
title: Get Staking/Delegation Events
excerpt: Get all delegation/staking/alpha buys&sells.
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
      "id": "finney-108-0x40c47b6a294686fe9612b5d78dd369f4c77fa3bbf96a4286ede97410ba2e3209-0xa4d9f9bfd193ceba1b0fb87d66fd53bfe454305aa3118bcb3552e90f13af7f2c-6226777-66",
      "block_number": 6226777,
      "timestamp": "2025-08-15T16:36:12Z",
      "action": "DELEGATE",
      "nominator": {
        "ss58": "5FnrTnBvPmVFw4FeQHePJyrvsuK8EkXxYxk1EBwpEPmKsdtg",
        "hex": "0xa4d9f9bfd193ceba1b0fb87d66fd53bfe454305aa3118bcb3552e90f13af7f2c"
      },
      "delegate": {
        "ss58": "5DXdHixxtCvoa6GHKs2Jgrdzc61882Ftx1zN2sYFQuwgL1S1",
        "hex": "0x40c47b6a294686fe9612b5d78dd369f4c77fa3bbf96a4286ede97410ba2e3209"
      },
      "amount": "1750000000",
      "alpha": "1005293226196",
      "usd": "636.46",
      "alpha_price_in_tao": "0.00174078562791271212",
      "alpha_price_in_usd": "0.63",
      "slippage": "0.376975328288734945",
      "fee": "881208",
      "netuid": 108,
      "extrinsic_id": "6226777-0016",
      "is_transfer": null,
      "transfer_address": null
    },
```