---
title: Get Slippage
excerpt: Estimate the slippage for an alpha/tao transaction.
api:
  file: taostats-1.json
  operationId: get-slippage
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

<br />

```
{
  "netuid": 19,
  "block_number": 5453605,
  "timestamp": "2025-04-28T23:14:36Z",
  "alpha_price": "0.0695548637", price in tao
  "output_tokens": "14376501457", output tokens received as rao
  "expected_output_tokens": "14377139805", tokens expected as rao
  "diff": "638347", Difference in roa
  "slippage": "0.0044400105" slippage as value
}
```