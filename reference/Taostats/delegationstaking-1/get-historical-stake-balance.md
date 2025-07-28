---
title: Get dTao Historical Stake Balance
excerpt: ''
api:
  file: taostats-1.json
  operationId: get-historical-stake-balance
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
      "block_number": 5453657,
      "timestamp": "2025-04-28T23:25:00.001Z",
      "hotkey_name": "TAO.app",
      "hotkey": {
        "ss58": "5CoZxgtfhcJKX2HmkwnsN18KbaT9aih9eF3b6qVPTgAUbifj",
        "hex": "0x20b0f8ac1d5416d32f5a552f98b570f06e8392ccb803029e04f63fbe0553c954"
      },
      "coldkey": {
        "ss58": "5HqaAYanMmQUh6agtnsXeWcHJDsoBF4eWwAkUPV7WEG3zZqW",
        "hex": "0xff65514f004c0bc475af33c478c36c2fe74c7e3d107937a0b74e781de7d4cfa1"
      },
      "netuid": 0,
      "subnet_rank": 88, wallet rank in subnet
      "subnet_total_holders": 42984, total holders in subnet
      "balance": "13797839517232", alpha balance as rao
      "balance_as_tao": "13797839517232" tao balance as rao
    },
```