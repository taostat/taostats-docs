---
title: Getting Started With Taostats API
excerpt: This page will help you get started with TaoStats.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
The Taostats API v0 consists of two very simple APIs



# Bittensor data

The /data.json endpoint returns an array of current Bittensor data. Updated every 5 minutes.

```curl
curl --request GET \
     --url https://taostats.io/data.json \
```



```json
[
  {
    "network": "Bittensor",
    "token": "TAO",
    "price": "444.2",
    "24h_change": "-1.98",
    "24h_volume": "23462034.839452",
    "current_supply": "6156688",
    "total_supply": "21000000",
    "delegated_supply": "5500423",
    "market_cap": "2734815638",
    "next_halvening": "26 September 2025",
    "daily_return_per_1000t": "0.0010733719933903",
    "validating_apy": "19.6",
    "staking_apy": "16.07",
    "last_updated": "01 February 2024 14:05:23 GMT"
  }
]
```

# Tao Supply

Simplified from Bittensor Data to return ONLY the integer of Bittensor supply.

```curl
curl --request GET \
     --url https://taostats.io/data-current-supply.json \
```

```
6156688
```