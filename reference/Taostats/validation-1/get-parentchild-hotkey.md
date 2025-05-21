---
title: Get Parent/Child Hotkey History
excerpt: ''
api:
  file: taostats-1.json
  operationId: get-parentchild-hotkey
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

```json
{
  "hotkey": {
    "ss58": "5F2CsUDVbRbVMXTh9fAzF9GacjVX7UapvRxidrxe7z8BYckQ",
    "hex": "0x82cca2238d379e49d84e9e1b8df35dd496d6a8b4ca4f511ac9e38fa04d42f86b"
  },
  "coldkey": {
    "ss58": "5CMEwRYLefRmtJg7zzRyJtcXrQqmspr9B1r1nKySDReA37Z1",
    "hex": "0x0c9c8ec969246de9771893dd7e89e5e70483e860c45359b3223cd01d598f0c7d"
  },
  "block_number": 5454180,
  "timestamp": "2025-04-29T01:09:36Z",
  "netuid": 1,
  "stake": "0",
  "family_stake": "0",
  "take": "0.08999771114671549554",
  "childkey_take": "0.08999771114671549554",
  "children": [],
  "parents": [
    {
      "hotkey": {
        "ss58": "5FFM6Nvvm78GqyMratgXXvjbqZPi7SHgSQ81nyS96jBuUWgt",
        "hex": "0x8cd280d43e4cf6501ae3b425583975ff63ce4d7470cf518074b5903ff375600e"
      },
      "coldkey": {
        "ss58": "5GyAMYSxde6x5hG8AHksoPHZZeum8GXk8sXisgADNn6CSi7Y",
        "hex": "0xd8f2e4fd7f807350f5188664c1831fa3d6872af51fdb660876af0eeea7a9aa55"
      },
      "stake": "0",
      "family_stake": "0",
      "take": "0.17999542229343099107",
      "childkey_take": "0",
      "proportion": "1",
      "proportion_staked": "0",
      "root_weight": "0.17999999999999999996",
      "root_stake": "34905835585091",
      "alpha_stake": "56454414461",
      "root_stake_as_alpha": "6283050405316.3799986037665766",
      "total_alpha_stake": "6339504819777.3799986037665766",
      "family_root_stake": "0",
      "family_alpha_stake": "0",
      "family_root_stake_as_alpha": "0.37999860376657659636",
      "family_total_alpha_stake": "0.37999860376657659636",
      "proportion_root_stake": "34905835585091",
      "proportion_alpha_stake": "56454414461",
      "proportion_root_stake_as_alpha": "6283050405316",
      "proportion_total_alpha_stake": "6339504819777"
    },
    {
      "hotkey": {
        "ss58": "5F27Eqz2PhyMtGMEce898x31DokNqRVxkm5AhDDe6rDGNvoY",
        "hex": "0x82b9ad19799ddb1bf0c237ee5f0c4726d5c2ad27d71d2c276ee20d31b5391c37"
      },
      "coldkey": {
        "ss58": "5GYXZBZoFA74nzAGg4R9omd2SfCDHiGufETtrLso6BRzv2p4",
        "hex": "0xc6292094723749e68a8a8adbb40029a94e18e704c44b9f2400d50f6f3d496f7b"
      },
      "stake": "0",
      "family_stake": "0",
      "take": "0.17999542229343099107",
      "childkey_take": "0",
      "proportion": "1",
      "proportion_staked": "0",
      "root_weight": "0.17999999999999999996",
      "root_stake": "29004429387691",
      "alpha_stake": "123211789161",
      "root_stake_as_alpha": "5220797289784.3799988398228245",
      "total_alpha_stake": "5344009078945.3799988398228245",
      "family_root_stake": "0",
      "family_alpha_stake": "0",
      "family_root_stake_as_alpha": "0.37999883982282449236",
      "family_total_alpha_stake": "0.37999883982282449236",
      "proportion_root_stake": "29004429387691",
      "proportion_alpha_stake": "123211789161",
      "proportion_root_stake_as_alpha": "5220797289784",
      "proportion_total_alpha_stake": "5344009078945"
    },
    {
      "hotkey": {
        "ss58": "5H66JLTYFWaHDtBtScE4X9f5WDjrBS1iGeXeRykPuH3SMyNh",
        "hex": "0xde3bf6047f6ee3cf426eded6fc9defe563c4d3429b5fdb6cda4127d24cf7742c"
      },
      "coldkey": {
        "ss58": "5C8JS6BJ2SqbwxvxtmZ9HWQ6wqPSNpxoKYpVS87bCnD4rcWk",
        "hex": "0x02be21535cb9b0b3a3e86c9cdb923cf87ef18caed5a754db42d9ca49e5e12729"
      },
      "stake": "0",
      "family_stake": "0",
      "take": "0.17999542229343099107",
      "childkey_take": "0",
      "proportion": "1",
      "proportion_staked": "0",
      "root_weight": "0.17999999999999999996",
      "root_stake": "717552",
      "alpha_stake": "91191378794",
      "root_stake_as_alpha": "129159.35999999999997129792",
      "total_alpha_stake": "91191507953.35999999999997130",
      "family_root_stake": "0",
      "family_alpha_stake": "0",
      "family_root_stake_as_alpha": "0.35999999999997129792",
      "family_total_alpha_stake": "0.35999999999997129792",
      "proportion_root_stake": "717552",
      "proportion_alpha_stake": "91191378794",
      "proportion_root_stake_as_alpha": "129159",
      "proportion_total_alpha_stake": "91191507953"
    }
  ],
  "root_weight": "0.17999999999999999996",
  "root_stake": "162117222637484",
  "alpha_stake": "15770304489972",
  "root_stake_as_alpha": "29181100074747.119993515311094",
  "total_alpha_stake": "44951404564719.119993515311094",
  "family_root_stake": "226027488327818",
  "family_alpha_stake": "16041162072388",
  "family_root_stake_as_alpha": "40684947899006.119993515311094",
  "family_total_alpha_stake": "56726109971394.119993515311094"
}
```