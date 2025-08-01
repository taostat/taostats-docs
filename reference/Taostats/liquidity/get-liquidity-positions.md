---
title: Get Liquidity Positions
excerpt: Get all of the Liquidity positions.
api:
  file: taostats-1.json
  operationId: get_apidtaoliquiditypositionv1
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
## Response Example

<br />

```
    {
      "id": "403",
      "coldkey": {
        "ss58": "5CUhxSDwhsAiB3bcdtwUe2mJDmQhJDS28CspkpoQ38fkSQLs",
        "hex": "0x124e397358cdcb1c4c29e274134072f67c906d235b2b95cf18ee79bf4320f92e"
      },
      "netuid": 73,
      "liquidity": "18944271910",
      "tick_low": -62150,
      "tick_high": -59918,
      "tao": "100017390",
      "alpha": "0",
      "max_price": "0.0024999102944514884633696779",
      "min_price": "0.0019998376620029202652596757",
      "tao_committed": "100017390",
      "alpha_committed": "0",
      "tao_withdrawn": "0",
      "alpha_withdrawn": "0",
      "fees_claimed_tao": "0",
      "fees_claimed_alpha": "0",
      "block_number": 6126587,
      "timestamp": "2025-08-01T18:38:12Z",
      "opened_block_number": 6126587,
      "opened_timestamp": "2025-08-01T18:38:12Z",
      "last_modified_block_number": null,
      "last_modified_timestamp": null,
      "closed_block_number": null,
      "closed_timestamp": null
    }
```