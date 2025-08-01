---
title: Get Parent/Child Hotkey History
excerpt: Historical Parent & Child relationships for validators
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
        "ss58": "5GKH9FPPnWSUoeeTJp19wVtd84XqFW4pyK2ijV2GsFbhTrP1",
        "hex": "0xbc0e6b701243978c1fe73d721c7b157943a713fca9f3c88cad7a9f7799bc6b26"
      },
      "coldkey": {
        "ss58": "5GcCZ2BPXBjgG88tXJCEtkbdg2hNrPbL4EFfbiVRvBZdSQDC",
        "hex": "0xc8f623c92b47ac9645d6744f3d448cdb7a2a3b08a22a39bfd1db0afbd9c07117"
      },
      "block_number": 5657375,
      "timestamp": "2025-05-28T14:18:36Z",
      "netuid": 76,
      "stake": "0",
      "family_stake": "0",
      "take": "0.08999771114671549554",
      "childkey_take": "0",
      "children": [
        {
          "hotkey": {
            "ss58": "5FFApaS75bv5pJHfAp2FVLBj9ZaXuFDjEypsaBNc1wCfe52v",
            "hex": "0x8cafec513739d2ed72700fe9ef1b4a62c3d0b06ddf6258bb00cbac2cbced5f68"
          },
          "coldkey": {
            "ss58": "5GZSAgaVGQqegjhEkxpJjpSVLVmNnE2vx2PFLzr7kBBMKpGQ",
            "hex": "0xc6da3c3be1d3c3863640ade174ca1463b019e1b5bdafed225b40f1507fe41a67"
          },
          "stake": "0",
          "family_stake": "0",
          "take": "0.08999771114671549554",
          "childkey_take": "0.0199893186846723125",
          "proportion": "1",
          "proportion_staked": "0",
          "root_weight": "0.17999999999999999996",
          "root_stake": "386510462928135",
          "alpha_stake": "120571332930478",
          "root_stake_as_alpha": "69571883327064.299984539581483",
          "total_alpha_stake": "190143216257542.29998453958148",
          "family_root_stake": "3917406108124717",
          "family_alpha_stake": "243382747770627",
          "family_root_stake_as_alpha": "705133099462450.29998453958148",
          "family_total_alpha_stake": "948515847233077.2999845395815",
          "proportion_root_stake": "806561659011751",
          "proportion_alpha_stake": "68802609494413",
          "proportion_root_stake_as_alpha": "145181098622115",
          "proportion_total_alpha_stake": "213983708116528"
        }
      ],
      "parents": [],
      "root_weight": "0.17999999999999999996",
      "root_stake": "806561659011751",
      "alpha_stake": "68802609494413",
      "root_stake_as_alpha": "145181098622115.17996773753364",
      "total_alpha_stake": "213983708116528.17996773753364",
      "family_root_stake": "0",
      "family_alpha_stake": "0",
      "family_root_stake_as_alpha": "0.17996773753363952996",
      "family_total_alpha_stake": "0.17996773753363952996"
    }
```