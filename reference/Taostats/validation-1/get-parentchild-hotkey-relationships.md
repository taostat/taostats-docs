---
title: Get Parent/Child hotkey relationships
excerpt: ''
api:
  file: taostats-1.json
  operationId: get-parentchild-hotkey-relationships
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
      "block_number": 5657365,
      "timestamp": "2025-05-28T14:16:36Z",
      "netuid": 1,
      "stake": "0",
      "family_stake": "0",
      "take": "0.08999771114671549554",
      "childkey_take": "0.04499885557335774777",
      "children": [
        {
          "hotkey": {
            "ss58": "5Cg5QgjMfRqBC6bh8X4PDbQi7UzVRn9eyWXsB8gkyfppFPPy",
            "hex": "0x1afa23c44b7863043b019fd8e8c32e788ea1499a2aad8321a2173cc1969b890d"
          },
          "coldkey": {
            "ss58": "5FRXwb2qsEhqDQQKcm5m2MF26xTWwW65MHTEtKFFydypuqjG",
            "hex": "0x949779f12e592b9f926fa67789c27d8af886b12199733a0ba2ea13167057da73"
          },
          "stake": "0",
          "family_stake": "0",
          "take": "0.17999542229343099107",
          "childkey_take": "0",
          "proportion": "1",
          "proportion_staked": "0",
          "root_weight": "0.17999999999999999996",
          "root_stake": "4511060876",
          "alpha_stake": "152664747453572",
          "root_stake_as_alpha": "811990957.6799999998195575650",
          "total_alpha_stake": "152665559444529.67999999981956",
          "family_root_stake": "3163875605042241",
          "family_alpha_stake": "431395842280023",
          "family_root_stake_as_alpha": "569497608907604.67999999981956",
          "family_total_alpha_stake": "1000893451187626.6799999998196",
          "proportion_root_stake": "806561659011751",
          "proportion_alpha_stake": "53000048114643",
          "proportion_root_stake_as_alpha": "145181098622115",
          "proportion_total_alpha_stake": "198181146736758"
        }
      ],
      "parents": [
        {
          "hotkey": {
            "ss58": "5GmvyePN9aYErXBBhBnxZKGoGk4LKZApE4NkaSzW62CYCYNA",
            "hex": "0xd0622986d748433d484b9b351b9a38737ee869ef2a50b75e5f890bee2c3afb18"
          },
          "coldkey": {
            "ss58": "5Cyfk5Jjee6uCafjZyUUjtKd7Q4qh1yJ48Ts7bkT9xXaDqe1",
            "hex": "0x2864e4216dd67df21f445836da8f35faad206f526e214aaf9c3753e60b2c8a6b"
          },
          "stake": "0",
          "family_stake": "0",
          "take": "0.08999771114671549554",
          "childkey_take": "0",
          "proportion": "1",
          "proportion_staked": "0",
          "root_weight": "0.17999999999999999996",
          "root_stake": "12271250917581",
          "alpha_stake": "0",
          "root_stake_as_alpha": "2208825165164.5799995091499633",
          "total_alpha_stake": "2208825165164.5799995091499633",
          "family_root_stake": "0",
          "family_alpha_stake": "0",
          "family_root_stake_as_alpha": "-0.42000049085003670324",
          "family_total_alpha_stake": "-0.42000049085003670324",
          "proportion_root_stake": "12271250917581",
          "proportion_alpha_stake": "0",
          "proportion_root_stake_as_alpha": "2208825165165",
          "proportion_total_alpha_stake": "2208825165165"
        }
      ],
      "root_weight": "0.17999999999999999996",
      "root_stake": "806561659011751",
      "alpha_stake": "53000048114643",
      "root_stake_as_alpha": "145181098622115.17996773753364",
      "total_alpha_stake": "198181146736758.17996773753364",
      "family_root_stake": "12271250917581",
      "family_alpha_stake": "0",
      "family_root_stake_as_alpha": "2208825165165.1799677375336395",
      "family_total_alpha_stake": "2208825165165.1799677375336395"
    }
```