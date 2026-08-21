---
title: What is Commit Reveal?
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

Designed to stop weight copying: weights are committed to the chain, but revealed several epochs later.

Commit Reveal 3.0 launched in December 2024.

Commit Reveal is designed to stop weight copying validators. See [Weight Copying](/docs/weight-copying)

For subnets that support Commit Reveal, all weights submitted by validators will be encrypted for a number of epochs.  The weights will only be revealed and used for Yuma Consensus upon decryption.  If a validator is weight copying, the are only able to access stale data. This will lower their score, making weight copying less lucrative.

# Setting Up Commit Reveal

Subnet owners have two new Subnet Hyperparameters:

```shell
 commit_reveal_weights_interval   1                      1               
 commit_reveal_weights_enabled    False                  False           

```

Enabling and setting the number of intervals will turn on Commit Reveal for the subnet.  Interval denotes the number of tempos until the weights will be revealed.  If set to 3, the weights will be revealed in three tempos, at the start of the tempo.

# Setting Weights

Validators do nothing different post Commit Reveal.  The chain nodes establish if Commit Reveal is turned on. If CR is on, the submitted weights are time-lock encrypted (using drand/tlock) and the encrypted commit is placed on chain.  The encryption is bound to a future round, so the weights automatically become decryptable once the reveal interval (`commit_reveal_weights_interval` epochs) has elapsed — there is no hash-compare step; the chain simply decrypts and applies them at that point.

# Miner ramifications

If you make changes to your miner, the resulting scores will be delayed by several epochs:

## New Miner

Epoch 1: Start a miner, evaluated by all the miners.

Epoch 2: Validators place initial weights

Epoch 2 + `commit_reveal_weights_interval`: your initial weight appears.

## Miner crashes

Epoch x: Miner crashes. Stops responding to validator requests

Epoch x+1: Validators begin lowering your score

(intervening epochs - scores continue to drop precipitously)

Epoch x+1+ `commit_reveal_weights_interval`: you start seeing dropped scores

Miners should not be using validator scores to determine if their miners are active.  With Commit Reveal, deregistration is almost guaranteed.
