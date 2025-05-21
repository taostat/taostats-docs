---
title: Multisig extrinsics
excerpt: Organizations can protect their wallets with multi-signature wallets
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
A multisignature wallet account requires several wallet accounts to sign off on any transaction that might take place.  This is very useful for organizations - it increases security and distributes control of the account from one password to multiple passwords.

There are tutorials on how to create and use multisig accounts at [polkadot.js](https://support.polkadot.network/support/solutions/articles/65000181826-how-to-create-and-use-a-multisig-account) 

In this tutorial, we will look at the extrinsics that are created during a multisig event on chain. There are three events

- Multisig.as_multi
- Multisig.approve_as_multi
- Multisig.cancel_as_multi

<br />

# The three stages of a multisig operation

- **Start of the operation**:  Either `Multisig.as_multi` or `Multisig.approve_as_multi` may kick off the operation.  
  - In this step a `threshold` is set. This is the number of sigs required for the operation to be completed.
    - If the `Multisig.as_multi` is called, `[args][call]`  describes the extrinsics to be processed on chain upon completion.
    - If the `Multisig.approve_as_multi` is called,  \``[args][callHash]` is a hash that describes the extrinsics to be completed.
  - A fee is paid when completing a multisig process.  This will be deducted from the coldkey of the wallet starting the multisig process.
- **Collect signatures** In this step, subsequent calls are collected to reach the threshold.  These can be `Multisig.as_multi` or `Multisig.approve_as_multi` calls.
  - These transactions contain a `maybeTimepoint` argument with two parameters to connect with the inital multisig call. 
    - `height` the block number of the original call.
    - `index` The exttrinsic index of the original call.
- **Complete the operation**. Either `Multisig.as_multi` or `Multisig.cancel` completes the operation.
  - `Multisig.as_multi` - completes the operation as successful. The threshold has been reached, and the calls denoted will now be run on chain.
  - `Multisig.cancel_as_multi` - as probably expected, this will cancel.  
    - Cancel extrinsics have the `timepoint` extrinsic that matches the `maybeTimepoint` from the collection step.  On a cancel step, this is required, so it is not "maybe" included in the extrinsic.
    - The fee is refunded to the key that kicked off the process.

# Examples

## Example 1:

In this example - more than `threshold` calls are made - because the last call _must_ be a `as_multi`. This multisig is being used to transfer 13.2 tao.

### Initial call

See it on Taostats: [4472647-0009](https://taostats.io/extrinsic/4472647-0009) 

```json
{
 "id": "4472647-0009",
  "extrinsic_id": "4472647-0009",
  "parent_id": null,
  "extrinsic_index": 9,
  "success": true,
  "error": null,
  "pallet": "Multisig",
  "name": "approve_as_multi",
  "full_name": "Multisig.approve_as_multi",
  "args": {
    "callHash": "0x536a4ae2fe64d59a3b8a4fa4f9db38c728aa1f8216570d69b1be6274b6b50fdc",
    "maxWeight": {
      "proofSize": "0",
      "refTime": "0"
    },
    "otherSignatories": [
      "0x34fff9eeda79435aba922eb7af06924065d9a96f516093bc6801009c4317ae56",
      "0xd0a9c979be7514edc82b8f41d096212f8d5a2aacce2ddfe87a7f8ed1d9e06e55"
    ],
    "threshold": 2
  },
  "origin": {
    "__kind": "system",
    "value": {
      "__kind": "Signed",
      "value": "0xa2d7f3250155801ebfae9c5cc0d522a479d9110499630409be004a5b53838c34"
    }
  },
  "origin_address": "0xa2d7f3250155801ebfae9c5cc0d522a479d9110499630409be004a5b53838c34",
  "timestamp": "2024-12-13T13:18:00Z",
  "block_number": 4472647
  },
```

In this initial call, the `approve_as_multi` is called. The signer of the extrinsic can be found in `origin_address`. There is a `threshold` of two - meaning one additional signature is required (and there are two `args/otherSignatories` that are eligible to complete the process).

### Second call

See it on Taostats: [4472648-0009](https://taostats.io/extrinsic/4472648-0009) 

```json
{
  "id": "4472648-0009",
  "extrinsic_id": "4472648-0009",
  "parent_id": null,
  "extrinsic_index": 9,
  "success": true,
  "error": null,
  "pallet": "Multisig",
  "name": "approve_as_multi",
  "full_name": "Multisig.approve_as_multi",
  "args": {
    "callHash": "0x536a4ae2fe64d59a3b8a4fa4f9db38c728aa1f8216570d69b1be6274b6b50fdc",
    "maxWeight": {
      "proofSize": "0",
      "refTime": "0"
    },
    "maybeTimepoint": {
      "height": 4472647,
      "index": 9
    },
    "otherSignatories": [
      "0x34fff9eeda79435aba922eb7af06924065d9a96f516093bc6801009c4317ae56",
      "0xa2d7f3250155801ebfae9c5cc0d522a479d9110499630409be004a5b53838c34"
    ],
    "threshold": 2
  },
  "origin": {
    "__kind": "system",
    "value": {
      "__kind": "Signed",
      "value": "0xd0a9c979be7514edc82b8f41d096212f8d5a2aacce2ddfe87a7f8ed1d9e06e55"
    }
  },
  "origin_address": "0xd0a9c979be7514edc82b8f41d096212f8d5a2aacce2ddfe87a7f8ed1d9e06e55",
  "timestamp": "2024-12-13T13:18:12Z",
  "block_number": 4472648
}
```

The second call is also `approve_as_multi`.  It is matched to the first call by the extrinsic:

```
"maybeTimepoint": {
  "height": 4472647,
  "index": 9
},
```

We can see that the `origin_address` matches one of the other_signatories in the first call.

> 📘 Threshold
> 
> The threshold for this Multisig process is 2, and this is the 2nd signature.
> 
> **BUT** The final multisig event **must be** a Multisig.as_multi. So this extrinsic does not complete the Multisig.

### Third call

See it on Taostats: [4472650-0006](https://taostats.io/extrinsic/4472650-0006) 

```json
{
            "id": "4472650-0006",
            "extrinsic_id": "4472650-0006",
            "parent_id": null,
            "extrinsic_index": 6,
            "success": true,
            "error": null,
            "pallet": "Multisig",
            "name": "as_multi",
            "full_name": "Multisig.as_multi",
            "args": {
                "call": {
                    "__kind": "Utility",
                    "value": {
                        "__kind": "batch_all",
                        "calls": [
                            {
                                "__kind": "Balances",
                                "value": {
                                    "__kind": "transfer_keep_alive",
                                    "dest": {
                                        "__kind": "Id",
                                        "value": "0xf02df68b1a1a9f72d868ee45c53e3a215abaaa1bb01b1f400aee16829547554e"
                                    },
                                    "value": "13268437943"
                                }
                            },
                            {
                                "__kind": "System",
                                "value": {
                                    "__kind": "remark",
                                    "remark": "0x312d3078343061356638666237633661383839643765343563396636346566343830326233313238363831383932613633636439616633376330666539393263626334352d313934"
                                }
                            }
                        ]
                    }
                },
                "maxWeight": {
                    "proofSize": "8811",
                    "refTime": "322610689"
                },
                "maybeTimepoint": {
                    "height": 4472647,
                    "index": 9
                },
                "otherSignatories": [
                    "0x34fff9eeda79435aba922eb7af06924065d9a96f516093bc6801009c4317ae56",
                    "0xd0a9c979be7514edc82b8f41d096212f8d5a2aacce2ddfe87a7f8ed1d9e06e55"
                ],
                "threshold": 2
            },
            "origin": {
                "__kind": "system",
                "value": {
                    "__kind": "Signed",
                    "value": "0xa2d7f3250155801ebfae9c5cc0d522a479d9110499630409be004a5b53838c34"
                }
            },
            "origin_address": "0xa2d7f3250155801ebfae9c5cc0d522a479d9110499630409be004a5b53838c34",
            "timestamp": "2024-12-13T13:18:36.001Z",
            "block_number": 4472650
        }
```

This is a `multisig.as_multi` and can conclude the multisig process.  Note that the `origin_address` matches the `otherSignatories` from the previous calls, and the `maybeTimepoint` also references the original multisig call.

We can finally see the extrinsics to be processed.  A transfer of `13268437943`rao (13.27 tao) to wallet address `0xf02df68b1a1a9f72d868ee45c53e3a215abaaa1bb01b1f400aee16829547554e` will be processed now that the multisig has been completed.

## Example 2:

in this example, the owners of Subnet 52 are setting the maximum registration cost to 8 tao.

### First call:

This call sets the threshold at 2, and lists 3 other possible signers of the multisig:

See it on Taostats: [4470399-0007](https://taostats.io/extrinsic/4470399-0007?network=finney) 

```json
 "id": "4470399-0007",
        "extrinsic_id": "4470399-0007",
        "parent_id": null,
        "extrinsic_index": 7,
        "success": true,
        "error": null,
        "pallet": "Multisig",
        "name": "approve_as_multi",
        "full_name": "Multisig.approve_as_multi",
        "args": {
            "callHash": "0x6a26028b812fbabfc55b511ad30d43d494f422380bda41bf770752a0d97fad84",
            "maxWeight": {
                "proofSize": "4697",
                "refTime": "171339000"
            },
            "otherSignatories": [
                "0x4aac8da05fd543a7289230071e07cf84472e879ee6f05a580c560eed0371aa78",
                "0x8ad144093c8b47c08d87a4e2c720f27a1261257ef38a206b2c32b873fb2a0540",
                "0x96f712f459001d62d24425d0515d406cc974485fc1184c6ff3de08ecfdcd1658"
            ],
            "threshold": 2
        },
        "origin": {
            "__kind": "system",
            "value": {
                "__kind": "Signed",
                "value": "0x7843fc4a1bcb721d7dd67e613c33936ecc46dc898662f8bbd5554d9a53c6014e"
            }
        },
        "origin_address": "0x7843fc4a1bcb721d7dd67e613c33936ecc46dc898662f8bbd5554d9a53c6014e",
        "timestamp": "2024-12-13T05:48:24Z",
        "block_number": 4470399
    }
```

### Second call:

The `maybeTimepoint` matches the block/extrinisic of the first call.  It is an `as_multi` call, and meets the threshold, so will complete the extrinsic.

This call also exposes the calls that will be processed on chain - `Admin.sudo_set_max_burn`, which is used to set the max registration cost for a subnet. In thi9s case, SN 52 now has a maximum registration of 8 tao.

See it on Taostats: [4470428-0008](https://taostats.io/extrinsic/4470428-0008) 

```json
        {
            "id": "4470428-0008",
            "extrinsic_id": "4470428-0008",
            "parent_id": null,
            "extrinsic_index": 8,
            "success": true,
            "error": null,
            "pallet": "Multisig",
            "name": "as_multi",
            "full_name": "Multisig.as_multi",
            "args": {
                "call": {
                    "__kind": "AdminUtils",
                    "value": {
                        "__kind": "sudo_set_max_burn",
                        "maxBurn": "800000000",
                        "netuid": 52
                    }
                },
                "maxWeight": {
                    "proofSize": "4697",
                    "refTime": "171339000"
                },
                "maybeTimepoint": {
                    "height": 4470399,
                    "index": 7
                },
                "otherSignatories": [
                    "0x7843fc4a1bcb721d7dd67e613c33936ecc46dc898662f8bbd5554d9a53c6014e",
                    "0x8ad144093c8b47c08d87a4e2c720f27a1261257ef38a206b2c32b873fb2a0540",
                    "0x96f712f459001d62d24425d0515d406cc974485fc1184c6ff3de08ecfdcd1658"
                ],
                "threshold": 2
            },
            "origin": {
                "__kind": "system",
                "value": {
                    "__kind": "Signed",
                    "value": "0x4aac8da05fd543a7289230071e07cf84472e879ee6f05a580c560eed0371aa78"
                }
            },
            "origin_address": "0x4aac8da05fd543a7289230071e07cf84472e879ee6f05a580c560eed0371aa78",
            "timestamp": "2024-12-13T05:54:12Z",
            "block_number": 4470428
        }
```

## Example 3 (cancel)

### First call

See it on Taostats: [4445415-0007](https://taostats.io/extrinsic/4445415-0007) 

```json
{
  "id": "4445415-0007",
  "extrinsic_id": "4445415-0007",
  "parent_id": null,
  "extrinsic_index": 7,
  "success": true,
  "error": null,
  "pallet": "Multisig",
  "name": "approve_as_multi",
  "full_name": "Multisig.approve_as_multi",
  "args": {
    "callHash": "0x0320ac365c31a9b66cc4b6819034f9ee0b5d739f1abb46155a3b5b7a65048777",
    "maxWeight": {
      "proofSize": "12296",
      "refTime": "3118516090"
    },
    "otherSignatories": [
      "0x103d4c4ee677d68bf2c73f370adbd03e7cbfbd3285c319f3d4b914d6db54f635",
      "0x660a7a15ed4368f4c0a12a1e75a6725587934645db38c91e13900a76b495b87b"
    ],
    "threshold": 3
  },
  "origin": {
    "__kind": "system",
    "value": {
      "__kind": "Signed",
      "value": "0xa0a381c42a7e069869a2489164b7532911a685d7011596aec733c49a80dd3214"
    }
  },
  "origin_address": "0xa0a381c42a7e069869a2489164b7532911a685d7011596aec733c49a80dd3214",
  "timestamp": "2024-12-09T18:31:36Z",
  "block_number": 4445415
}
```

### Second Call

In the cancel call, `timepoint` connects to the initial extrinsic.  This will cancel the multisig process.

See it on Taostats: [4445425-0005](https://taostats.io/extrinsic/4445425-0005) 

<br />

```json
{  
    "id": "4445425-0005",  
    "extrinsic_id": "4445425-0005",  
    "parent_id": null,  
    "extrinsic_index": 5,  
    "success": true,  
    "error": null,  
    "pallet": "Multisig",  
    "name": "cancel_as_multi",  
    "full_name": "Multisig.cancel_as_multi",  
    "args": {  
      "callHash": "0x0320ac365c31a9b66cc4b6819034f9ee0b5d739f1abb46155a3b5b7a65048777",  
      "otherSignatories": [  
        "0x103d4c4ee677d68bf2c73f370adbd03e7cbfbd3285c319f3d4b914d6db54f635",  
        "0x660a7a15ed4368f4c0a12a1e75a6725587934645db38c91e13900a76b495b87b"  
      ],  
      "threshold": 3,  
      "timepoint": {  
        "height": 4445415,  
        "index": 7  
      }  
    },  
    "origin": {  
      "**kind": "system",  
      "value": {  
        "**kind": "Signed",  
        "value": "0xa0a381c42a7e069869a2489164b7532911a685d7011596aec733c49a80dd3214"  
      }  
    },  
    "origin_address": "0xa0a381c42a7e069869a2489164b7532911a685d7011596aec733c49a80dd3214",  
    "timestamp": "2024-12-09T18:33:36Z",  
    "block_number": 4445425  
  }
```