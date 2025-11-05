---
title: Get Stats Latest
excerpt: Get the latest high level stats from the chain.
api:
  file: taostats-1.json
  operationId: get-stats-latest
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
  "pagination": {
    "current_page": 1,
    "per_page": 1,
    "total_items": 1,
    "total_pages": 1,
    "next_page": null,
    "prev_page": null
  },
  "data": [
    {
      "block_number": 6812152,
      "timestamp": "2025-11-04T23:59:48Z",
      "issued": "10238806730295346",
      "staked": "7188376143978931",
      "staked_alpha": "1460542286310766",
      "staked_root": "5727829104805753",
      "staked_root_on_keep": "67086822569",
      "staked_root_on_swap": "5727762017983184",
      "subnet_locked": "12967601253620",
      "free": "3050779213817594",
      "accounts": 429138,
      "balance_holders": 246326,
      "extrinsics": 157639106,
      "transfers": 4510647,
      "subnets": 129,
      "subnet_registration_cost": "430905168626"
    }
  ]
}
```
