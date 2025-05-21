---
title: Get Account History
excerpt: Gives most recent coldkey balance (from the database)
api:
  file: taostats-1.json
  operationId: get-account-history
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
      "address": {
        "ss58": "5DCaUSocqajoo8v2936aPAGV5QBYdVhRBTLMoYUsuF8LqyEM",
        "hex": "0x323d57bfbf584d04cb390b4ade567aba4628b6d34b4484035ff6c2f9ee42c827"
      },
      "network": "finney",
      "block_number": 5403431,
      "timestamp": "2025-04-21T23:59:48Z",
      "rank": 0,
      "balance_free": "18466145" value in rao,
      "balance_staked": "99950089307" value in rao,
      "balance_staked_alpha_as_tao": "0" value in rao,
      "balance_staked_root": "99950089307" value in rao,
      "balance_total": "99968555452" value in rao,
      "balance_free_24hr_ago": null,
      "balance_staked_24hr_ago": null,
      "balance_staked_alpha_as_tao_24hr_ago": null,
      "balance_staked_root_24hr_ago": null,
      "balance_total_24hr_ago": null,
      "created_on_date": "2024-03-23",
      "created_on_network": "finney",
      "coldkey_swap": null
    },
```
