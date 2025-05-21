---
title: Get Account
excerpt: Gives most recent coldkey balance (from the database)
api:
  file: taostats-1.json
  operationId: get-account
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
        "ss58": "5Hd2ze5ug8n1bo3UCAcQsf66VNjKqGos8u6apNfzcU86pg4N",
        "hex": "0xf5d5714c084c112843aca74f8c498da06cc5a2d63153b825189baa51043b1f0b"
      },
      "network": "finney",
      "block_number": 5451353b,
      "timestamp": "2025-04-28T15:44:12Z",
      "rank": 1,
      "balance_free": "658285656729475" free tao as rao,
      "balance_staked": "0" total tao staked as rao,
      "balance_staked_alpha_as_tao": "0"tao staked in alpha as rao,
      "balance_staked_root": "0" tao staked to root as rao,
      "balance_total": "658285656729475" total balance as rao,
      "balance_free_24hr_ago": nul  balance change 24 hours (only populated with address in query),
      "balance_staked_24hr_ago": null (only populated with address in query),
      "balance_staked_alpha_as_tao_24hr_ago": null (only populated with address in query),
      "balance_staked_root_24hr_ago": null (only populated with address in query), 
      "balance_total_24hr_ago": null (only populated with address in query),
      "created_on_date": "2025-02-26" wallet creation date,
      "created_on_network": "finney",
      "coldkey_swap": null
    },
```
