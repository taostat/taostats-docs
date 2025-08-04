---
title: Get Validator History (pre-dtao)
excerpt: Get validator history pre Feb 13, 2025
api:
  file: taostats-1.json
  operationId: get-validator-history-1
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
      "hotkey": {
        "ss58": "5GKH9FPPnWSUoeeTJp19wVtd84XqFW4pyK2ijV2GsFbhTrP1",
        "hex": "0xbc0e6b701243978c1fe73d721c7b157943a713fca9f3c88cad7a9f7799bc6b26"
      },
      "coldkey": {
        "ss58": "5GcCZ2BPXBjgG88tXJCEtkbdg2hNrPbL4EFfbiVRvBZdSQDC",
        "hex": "0xc8f623c92b47ac9645d6744f3d448cdb7a2a3b08a22a39bfd1db0afbd9c07117"
      },
      "name": "Taostats & Corcel",
      "block_number": 4920349,
      "timestamp": "2025-02-13T21:40:24Z",
      "created_on_date": "2023-03-21",
      "rank": 1,
      "nominators": 6691,
      "nominators_24_hr_change": 5,
      "system_stake": "5864261013828190", as rao
      "stake": "767381773437417", as rao
      "stake_24_hr_change": "-3452405790344", as rao
      "dominance": "13.08573700297269211464",percentage
      "validator_stake": "457978988665",as rao
      "take": "0.08999771114671549554", number
      "total_daily_return": "0",
      "validator_return": "0",
      "nominator_return_per_k": "468470749",as rao
      "apr": "0.17099",
      "nominator_return_per_k_7_day_average": "468989538",as rao
      "nominator_return_per_k_30_day_average": "452990300" as rao,
      "apr_7_day_average": "0.17118",
      "apr_30_day_average": "0.16534",
      "pending_emission": "136028561110", per epoch as rao
      "blocks_until_next_reward": 4472,
      "last_reward_block": 4917621,
      "registrations": [
        0,
        <snip>
        63
      ],
      "permits": [
        0,
  <snip>
        53
      ],
      "subnet_dominance": [
        {
          "netuid": 0,
          "dominance": "13.08573700297269211464", percentage
          "family_stake": "767381773437417" as rao
        },
  <snip>
        }
      ]
    },
```