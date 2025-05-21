---
title: Get Validator Performance History (dTao)
excerpt: ''
api:
  file: taostats-1.json
  operationId: get-validator-performance-dtao-history
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
      "name": null, name in available
      "hotkey": {
        "ss58": "5CAQhe9pWMe9anWX9qbK6Z9RydRth7S6WDopapSr6uShGum5",
        "hex": "0x0459b8ac46933d4cbbd4f0b36934704e7a726851b359ca2ee8d5e704a8896e02"
      },
      "coldkey": {
        "ss58": "5GcCZ2BPXBjgG88tXJCEtkbdg2hNrPbL4EFfbiVRvBZdSQDC",
        "hex": "0xc8f623c92b47ac9645d6744f3d448cdb7a2a3b08a22a39bfd1db0afbd9c07117"
      },
      "block_number": 5457464,
      "timestamp": "2025-04-29T12:06:24Z",
      "netuid": 19,
      "uid": 142,
      "position": 1,
      "last_updated": 5457424,
      "nominators": 823,
      "vtrust": "0.99995422293430991073", as number
      "validator_type": "childkey",
      "take": "0.17999542229343099107", as number
      "childkey_take": "0", as number
      "proportion": "1",
      "subnet_weight": "410541579188894.74000000000000", as rao
      "root_weight": "217835913007812.74000000000000", as rao
      "alpha": "192705666181082", as rao
      "family_subnet_weight": "410541579188894.74000000000000", as rao
      "family_root_weight": "217835913007812.74000000000000", as rao
      "family_alpha": "192705666181082", as rao
      "dominance": "25.60", percentage
      "dividends": "0.26250095368886854353", as number
      "nominator_return_per_day": "0",
      "validator_return_per_day": "0"
    }  
```