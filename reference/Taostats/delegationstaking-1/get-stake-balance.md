---
title: Get Stake Balance
excerpt: ''
api:
  file: taostats-1.json
  operationId: get-stake-balance
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
      "hotkey_name": "Rizzo (Insured)",
      "hotkey": {
        "ss58": "5F2CsUDVbRbVMXTh9fAzF9GacjVX7UapvRxidrxe7z8BYckQ",
        "hex": "0x82cca2238d379e49d84e9e1b8df35dd496d6a8b4ca4f511ac9e38fa04d42f86b"
      },
      "coldkey": {
        "ss58": "5EqUG3oUuzT5siNv5bSE9PKzqp8t2ehYEX7SeEjTjymuJS9W",
        "hex": "0x7a9cbd27dd53d8020edb9db0a18c7603d12f8b64db91da1ce2d3909071a29656"
      },
      "netuid": 0,
      "subnet_rank": 88, wallet rank in subnet
      "subnet_total_holders": 42984, total holders in subnet
      "balance": "13797839517232", alpha balance as rao
      "balance_as_tao": "13797839517232" tao balance as rao
    },
```