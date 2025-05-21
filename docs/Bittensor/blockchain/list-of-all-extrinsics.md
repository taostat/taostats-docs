---
title: List of all Extrinsics
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Here is a list of all extrinsics that can be called on the Bittensor chain

# AdminUtils

## sudo_set_min_burn

Set the min cost for registering a neuron on a Subnet.

```
    {
      "id": "5214782-0006-0-0-16",
      "extrinsic_id": "5214782-0006",
      "parent_id": "5214782-0006-0-0",
      "extrinsic_index": 6,
      "success": true,
      "error": null,
      "pallet": "AdminUtils",
      "name": "sudo_set_min_burn",
      "full_name": "AdminUtils.sudo_set_min_burn",
      "args": {
        "minBurn": "500000",
        "netuid": 81
      },
      "origin": {
        "__kind": "system",
        "value": {
          "__kind": "Root"
        }
      },
      "origin_address": null,
      "timestamp": "2025-03-26T19:10:00Z",
      "block_number": 5214782
    },
```

## sudo_set_network_registration_allowed

Subnet owners can turn registration of neurons on and off

```
{
      "id": "5478134-0014",
      "extrinsic_id": "5478134-0014",
      "parent_id": null,
      "extrinsic_index": 14,
      "success": true,
      "error": null,
      "pallet": "AdminUtils",
      "name": "sudo_set_network_registration_allowed",
      "full_name": "AdminUtils.sudo_set_network_registration_allowed",
      "args": {
        "netuid": 93,
        "registrationAllowed": true
      },
      "origin": {
        "__kind": "system",
        "value": {
          "__kind": "Signed",
          "value": "0x90e03b40cb46b910f5087b33a545186ae038c64c4f1eeeefad5529c1ca8aaf02"
        }
      },
      "origin_address": "0x90e03b40cb46b910f5087b33a545186ae038c64c4f1eeeefad5529c1ca8aaf02",
      "timestamp": "2025-05-02T09:00:24Z",
      "block_number": 5478134
    },
```

## sudo_set_weights_version_key

<br />

<br />

# Balance

## transfer

<br />

## transfer_keep_alive

Transfer tao out of the wallet, but keep the wallet active if it is emptied.

```
{
      "id": "5430525-0016",
      "extrinsic_id": "5430525-0016",
      "parent_id": null,
      "extrinsic_index": 16,
      "success": true,
      "error": null,
      "pallet": "Balances",
      "name": "transfer_keep_alive",
      "full_name": "Balances.transfer_keep_alive",
      "args": {
        "dest": {
          "__kind": "Id",
          "value": "0x966823629376482d4e385481200b21c39ba8b03c3c9df1e6626aa360cc8d2d07"
        },
        "value": "5000000000"
      },
      "origin": {
        "__kind": "system",
        "value": {
          "__kind": "Signed",
          "value": "0x2c4e00e5e05300066520572235d3e2e726fa8981f0b5cc17b31a39aec9ae7018"
        }
      },
      "origin_address": "0x2c4e00e5e05300066520572235d3e2e726fa8981f0b5cc17b31a39aec9ae7018",
      "timestamp": "2025-04-25T18:18:36Z",
      "block_number": 5430525
    }
```

## transfer_all

Transfer everything out of the wallet

```
    {
      "id": "5430498-0015",
      "extrinsic_id": "5430498-0015",
      "parent_id": null,
      "extrinsic_index": 15,
      "success": true,
      "error": null,
      "pallet": "Balances",
      "name": "transfer_all",
      "full_name": "Balances.transfer_all",
      "args": {
        "dest": {
          "__kind": "Id",
          "value": "0x35ed58d459c3815ec3726b3e739bbe9c7955be7daa631a094006c614c6105055"
        },
        "keepAlive": false
      },
      "origin": {
        "__kind": "system",
        "value": {
          "__kind": "Signed",
          "value": "0xbe0c6455cdc7c07754108c65b96ead50b53b5c028599b92fb187e062a919d73e"
        }
      },
      "origin_address": "0xbe0c6455cdc7c07754108c65b96ead50b53b5c028599b92fb187e062a919d73e",
      "timestamp": "2025-04-25T18:13:12.001Z",
      "block_number": 5430498
    }
```

## transfer_allow_death

Transfer tao out of the wallet, and allow the wallet to be closed if emptied.

```
   {
      "id": "5430529-0012",
      "extrinsic_id": "5430529-0012",
      "parent_id": null,
      "extrinsic_index": 12,
      "success": true,
      "error": null,
      "pallet": "Balances",
      "name": "transfer_allow_death",
      "full_name": "Balances.transfer_allow_death",
      "args": {
        "dest": {
          "__kind": "Id",
          "value": "0x56daf75bd0f09c11d798263bc79baeb77c4b4af1dbd372bbe532b1f8702b2a7e"
        },
        "value": "1099809626"
      },
      "origin": {
        "__kind": "system",
        "value": {
          "__kind": "Signed",
          "value": "0x9aa26bf27530baa40c74c1f9f6e54669d0881d1f0c279567bd84a6f95e3c6b70"
        }
      },
      "origin_address": "0x9aa26bf27530baa40c74c1f9f6e54669d0881d1f0c279567bd84a6f95e3c6b70",
      "timestamp": "2025-04-25T18:19:24Z",
      "block_number": 5430529
    }
```

# Multisig

See our page on [Multisig extrinsics](doc:multisig-extrinsics)

# Proxy

## proxy

A proxy can run one or more commands for other wallets. The below extrinsic adds stake for a wallet.

```
 {
      "id": "5467505-0030",
      "extrinsic_id": "5467505-0030",
      "parent_id": null,
      "extrinsic_index": 30,
      "success": true,
      "error": null,
      "pallet": "Proxy",
      "name": "proxy",
      "full_name": "Proxy.proxy",
      "args": {
        "call": {
          "__kind": "SubtensorModule",
          "value": {
            "__kind": "add_stake_limit",
            "allowPartial": false,
            "amountStaked": "500000000",
            "hotkey": "0x2c36c8b88903c8507aa3a9a6dcfc016caf5cfd3d8bf755b97e63f8f8b7c56836",
            "limitPrice": "19687836523",
            "netuid": 98
          }
        },
        "real": {
          "__kind": "Id",
          "value": "0x0401ab945a33931436911328500ba51c95ede0bf6137bee326232d77b80a1560"
        }
      },
      "origin": {
        "__kind": "system",
        "value": {
          "__kind": "Signed",
          "value": "0x8c476f597851cba678abe6fd332cc926e1f31ac5a0ded0d7aeaf72cf638cfc34"
        }
      },
      "origin_address": "0x8c476f597851cba678abe6fd332cc926e1f31ac5a0ded0d7aeaf72cf638cfc34",
      "timestamp": "2025-04-30T21:34:36Z",
      "block_number": 5467505
    },
```

# SubtensorModule

## add_stake

Add stake to a subnet/validator combination.

0.1 alpha staked to 5F4tQyWrhfGVcNhoqeiNsR6KjD4wMZ2kfhLj4oHYuyHbZAc3 on Subnet 1.

```
    {
      "id": "5430500-0023",
      "extrinsic_id": "5430500-0023",
      "parent_id": null,
      "extrinsic_index": 23,
      "success": true,
      "error": null,
      "pallet": "SubtensorModule",
      "name": "add_stake",
      "full_name": "SubtensorModule.add_stake",
      "args": {
        "amountStaked": "100000000",
        "hotkey": "0x84d83d08ca89f8e60424ffa286f165c16dd8752e4faa4d8977221e6720678d28",
        "netuid": 1
      },
      "origin": {
        "__kind": "system",
        "value": {
          "__kind": "Signed",
          "value": "0x1814b2e94e436794c09d1f49e71df337a7b80a2d998d00ba55d8065282793958"
        }
      }
```

<br />

## burned_register

When a neuron is registered on a subnet.

Subnet 37 gained a new hotkey on block 5429414. The events will show the cost paid in tao, and the neuron registered,

```
    {
      "id": "5429414-0018",
      "extrinsic_id": "5429414-0018",
      "parent_id": null,
      "extrinsic_index": 18,
      "success": true,
      "error": null,
      "pallet": "SubtensorModule",
      "name": "burned_register",
      "full_name": "SubtensorModule.burned_register",
      "args": {
        "hotkey": "0x26eee8341ec943bc9c54814eee28a2a50ab9650d0a8d7b2fb989f5414f5d184d",
        "netuid": 37
      },
      "origin": {
        "__kind": "system",
        "value": {
          "__kind": "Signed",
          "value": "0x6248c90b832a5c0eb19ed7efeb04ce21ac32f1c51efc7a84d92f8ac342e4af19"
        }
      },
      "origin_address": "0x6248c90b832a5c0eb19ed7efeb04ce21ac32f1c51efc7a84d92f8ac342e4af19",
      "timestamp": "2025-04-25T14:36:24Z",
      "block_number": 5429414
    }
```

## faucet

Its turned off.  The chain on't just give you token....

```
  {
      "id": "5423845-0030",
      "extrinsic_id": "5423845-0030",
      "parent_id": null,
      "extrinsic_index": 30,
      "success": false,
      "error": {
        "extra_info": "Faucet is disabled.",
        "name": "FaucetDisabled",
        "pallet": "subtensorModule"
      },...
```

## register_network

Register a Subnet

```
{
      "id": "5410917-0016",
      "extrinsic_id": "5410917-0016",
      "parent_id": null,
      "extrinsic_index": 16,
      "success": true,
      "error": null,
      "pallet": "SubtensorModule",
      "name": "register_network",
      "full_name": "SubtensorModule.register_network",
      "args": {
        "hotkey": "0x4029e02529a634f32d81d288748bd5ab985735c85a5b0ae6145fe26cf8c2114d"
      },
      "origin": {
        "__kind": "system",
        "value": {
          "__kind": "Signed",
          "value": "0x2e6f72f9f63c222a689fc90bac5cf1676f0e77cf958232285d059f99cf4cf141"
        }
      },
      "origin_address": "0x2e6f72f9f63c222a689fc90bac5cf1676f0e77cf958232285d059f99cf4cf141",
      "timestamp": "2025-04-23T00:57:00Z",
      "block_number": 5410917
    }
```

## register_network_with_identity

Registers a Subnet, and adds chain identity for the coldkey

```
   {
      "id": "5299805-0017",
      "extrinsic_id": "5299805-0017",
      "parent_id": null,
      "extrinsic_index": 17,
      "success": true,
      "error": null,
      "pallet": "SubtensorModule",
      "name": "register_network_with_identity",
      "full_name": "SubtensorModule.register_network_with_identity",
      "args": {
        "hotkey": "0xe82185dda3905aade7965781cd903b78b2bf33bfb3f63ec6b1e879f8df8ef448",
        "identity": {
          "additional": "0x",
          "description": "0x4f7074696d697a696e67207374616b696e672073747261746567696573",
          "discord": "0x",
          "githubRepo": "0x68747470733a2f2f6769746875622e636f6d2f6d6f6269757366756e642f7374616b696e67",
          "subnetContact": "0x",
          "subnetName": "0x53cf84ceb16b696e67",
          "subnetUrl": "0x68747470733a2f2f7374616b696e67616c7068612e636f6d"
        }
      }
```

## remove_stake

3 alpha unstaked from SN 13.  Note there is no limit preventing slippage or price changes

```
{
  "id": "5429704-0017",
  "extrinsic_id": "5429704-0017",
  "parent_id": null,
  "extrinsic_index": 17,
  "success": true,
  "error": null,
  "pallet": "SubtensorModule",
  "name": "remove_stake",
  "full_name": "SubtensorModule.remove_stake",
  "args": {
    "amountUnstaked": "3056641054",
    "hotkey": "0x4cf50a5ada0484c23d0403635d2283d656323abb72ed1e50072c0001c5784c37",
    "netuid": 13
  }
```

<br />

## remove_stake_limit

The remove stake limit has a price limit to prevent slippage or excessive price changes.

```
    {
      "id": "5429704-0019",
      "extrinsic_id": "5429704-0019",
      "parent_id": null,
      "extrinsic_index": 19,
      "success": true,
      "error": null,
      "pallet": "SubtensorModule",
      "name": "remove_stake_limit",
      "full_name": "SubtensorModule.remove_stake_limit",
      "args": {
        "allowPartial": true,
        "amountUnstaked": "16636745479",
        "hotkey": "0xf058923f56e7a50f63ed108509e652b6a5c628a9d840135ac5f17b7ac1ea4679",
        "limitPrice": "6009646",
        "netuid": 79
      }
```

## root register

Register your validator on root

```
    {
      "id": "5494193-0020",
      "extrinsic_id": "5494193-0020",
      "parent_id": null,
      "extrinsic_index": 20,
      "success": true,
      "error": null,
      "pallet": "SubtensorModule",
      "name": "root_register",
      "full_name": "SubtensorModule.root_register",
      "args": {
        "hotkey": "0xbae956aa0819c3552a5630394d37f62f9fe04ebc30b2fcc9d0427957c35d3a2a"
      },
      "origin": {
        "__kind": "system",
        "value": {
          "__kind": "Signed",
          "value": "0x90a0bf8c9b8f1aff328a45e3c07b15798adfa8893b1df96e014ea32faa72c166"
        }
      },
      "origin_address": "0x90a0bf8c9b8f1aff328a45e3c07b15798adfa8893b1df96e014ea32faa72c166",
      "timestamp": "2025-05-04T14:32:12Z",
      "block_number": 5494193
    },
```

<br />

## schedule_coldkey_swap

Deprecated. Last used in July 2024.

## serve_axon

Serve a Validaor or miner on the Subnet.

This is serving 108.171.215.138 on SN 81

```
      "id": "5429446-0019",
      "extrinsic_id": "5429446-0019",
      "parent_id": null,
      "extrinsic_index": 19,
      "success": true,
      "error": null,
      "pallet": "SubtensorModule",
      "name": "serve_axon",
      "full_name": "SubtensorModule.serve_axon",
      "args": {
        "ip": "1823201162",
        "ipType": 4,
        "netuid": 81,
        "placeholder1": 0,
        "placeholder2": 0,
        "port": 8888,
        "protocol": 4,
        "version": 9001000
      },
      "origin": {
        "__kind": "system",
        "value": {
          "__kind": "Signed",
          "value": "0x6a4cbdf46b5bee69088dae065a183ae56198b33edbe77ef8b954b19ba38a395a"
        }
      },
      "origin_address": "0x6a4cbdf46b5bee69088dae065a183ae56198b33edbe77ef8b954b19ba38a395a",
      "timestamp": "2025-04-25T14:42:48Z",
      "block_number": 5429446
```

To convert the string IPv4 to an address:

```python
import socket
import struct

def int_to_ip(ip_int):
    """Converts an integer to an IP address string."""
    return socket.inet_ntoa(struct.pack('!I', ip_int))

# Example usage:
ip_int_value = 1823201162
ip_address = int_to_ip(ip_int_value)
print(f"The IP address for {ip_int_value} is: {ip_address}")
```

<br />

## serve_prometheus

```
{
      "id": "5174886-0013",
      "extrinsic_id": "5174886-0013",
      "parent_id": null,
      "extrinsic_index": 13,
      "success": true,
      "error": null,
      "pallet": "SubtensorModule",
      "name": "serve_prometheus",
      "full_name": "SubtensorModule.serve_prometheus",
      "args": {
        "ip": "600199924",
        "ipType": 4,
        "netuid": 27,
        "port": 8091,
        "version": 184
      },
      "origin": {
        "__kind": "system",
        "value": {
          "__kind": "Signed",
          "value": "0x58aef7b1efb44806fe14c6c58d0c1eb634a59fd2513f0ced6f2d10e0569af40d"
        }
      },
```

## set_children

This sets 0xae66d26fed539fc501b4340faaef65e20feb0dbf388658997c034babad06bf43 ( 5G1NjW9YhXLadMWajvTkfcJy6up3yH2q1YzMXDTi6ijanChe) as the parent for taobot (0x56a9aee6291bd03ab6d36d4d13e2bebae7cd403518066c72fba1b417d6ddd748) on Subnet 14.

```
    {
      "id": "5430760-0008-1",
      "extrinsic_id": "5430760-0008",
      "parent_id": null,
      "extrinsic_index": 8,
      "success": true,
      "error": null,
      "pallet": "SubtensorModule",
      "name": "set_children",
      "full_name": "SubtensorModule.set_children",
      "args": {
        "children": [
          [
            "18446744073709551615",
            "0xae66d26fed539fc501b4340faaef65e20feb0dbf388658997c034babad06bf43"
          ]
        ],
        "hotkey": "0x56a9aee6291bd03ab6d36d4d13e2bebae7cd403518066c72fba1b417d6ddd748",
        "netuid": 14
      },
      "origin": {
        "__kind": "system",
        "value": {
          "__kind": "Signed",
          "value": "0xd4b3efa00c7f20e8e94f39d1bed97ce0cacceb122a09a9ca24dfda401710391b"
        }
      },
      "origin_address": "0xd4b3efa00c7f20e8e94f39d1bed97ce0cacceb122a09a9ca24dfda401710391b",
      "timestamp": "2025-04-25T19:05:36Z",
      "block_number": 5430760
    }
```

## set_root_weights

Deprecated. In dTao, root weights are no longer set.

## set_weights:

Used by validators to set weights on miners

```
  {
      "timestamp": "2025-04-25T13:52:24Z",
      "block_number": 5429194,
      "hash": "0xf0944ef068c128ab08096db0c9edeb792319708a700f27286572f41c38575e50",
      "id": "5429194-0021",
      "index": 21,
      "version": 4,
      "signature": {
        "address": {
          "__kind": "Id",
          "value": "0xc065b0c58caa8513e462626b8ffa894eda31c213fc71fb6a7beae5bdfff39149"
        },
        "signature": {
          "__kind": "Sr25519",
          "value": "0xe49070c45c2b3da768046a87baebed0dd068fbd0fe5b6b00979afd932fa017789dea585e71d8d7c9e7eb428f36ff68e7d7f847202467174bd7d826ba39365b8e"
        },
        "signedExtensions": {
          "chargeTransactionPayment": "0",
          "checkMetadataHash": {
            "mode": {
              "__kind": "Disabled"
            }
          },
          "checkMortality": {
            "__kind": "Mortal114",
            "value": 0
          },
          "checkNonce": 17328
        }
      },
      "signer_address": "0xc065b0c58caa8513e462626b8ffa894eda31c213fc71fb6a7beae5bdfff39149",
      "tip": "0",
      "fee": "0",
      "success": true,
      "error": null,
      "call_id": "5429194-0021",
      "full_name": "SubtensorModule.set_weights",
      "call_args": {
        "dests": [
          <list of UIDs in the subnet>
        ],
        "netuid": 33,
        "versionKey": "2125",
        "weights": [
 						<list of weights>
        ]
      }
    }
```

# Utility

## [batch](doc:batch-extrinsics)

## [batch_all](doc:batch-extrinsics)

## [force_batch](doc:batch-extrinsics)