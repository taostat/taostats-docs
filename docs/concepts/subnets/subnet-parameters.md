---
title: Hyperparameter descriptions
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

In addition to miners and validator code, each subnet has a set of hyperparameters that define how it will interact with the bittensor network.

## Full hyperparameter reference

The canonical, current list of subnet hyperparameters (as of the latest chain release). **Owner-settable** shows whether the subnet owner can change the value themselves (`✅ yes`) or whether it is `sudo only` (governance / sudo-controlled). Read the live values for a subnet with `btcli sudo get --netuid <N>`; owners change the owner-settable ones with `btcli sudo set`.

> 📘 This table is reconciled against the official chain docs ([RaoFoundation/subtensor](https://github.com/RaoFoundation/subtensor)) and regenerated on each chain release. If a parameter here doesn't match what `btcli` returns, the chain is the source of truth — flag it and we'll re-sync.

| Hyperparameter | Unit | Owner-settable | What it controls |
|---|---|---|---|
| `rho` | integer | ✅ yes | trust curve steepness |
| `kappa` | fraction (u16, 65535 = 1.0) | sudo only | consensus majority-stake threshold |
| `immunity_period` | blocks (12s) | ✅ yes | prune-immunity window for new neurons |
| `min_allowed_weights` | integer | ✅ yes | minimum weights per submission |
| `max_weights_limit` | fraction (u16, 65535 = 1.0) | sudo only | cap on a single miner's weight |
| `tempo` | blocks (12s) | ✅ yes | blocks per consensus epoch |
| `min_difficulty` | PoW difficulty (u64) | sudo only | PoW registration difficulty floor |
| `max_difficulty` | PoW difficulty (u64) | ✅ yes | PoW registration difficulty ceiling |
| `difficulty` | PoW difficulty (u64) | sudo only | current PoW registration difficulty |
| `weights_version` | integer | ✅ yes | minimum version key for set_weights |
| `weights_rate_limit` | blocks (12s) | sudo only | wait between weight submissions |
| `adjustment_interval` | blocks (12s) | sudo only | difficulty/burn adjustment cadence |
| `activity_cutoff` | blocks (12s) | sudo only | no-weights window before inactive |
| `activity_cutoff_factor` | integer | ✅ yes | activity cutoff, per-mille of tempo |
| `registration_allowed` | flag | sudo only | new neuron registrations allowed |
| `network_pow_registration_allowed` | flag | ✅ yes | PoW registration toggle |
| `target_regs_per_interval` | integer | sudo only | registration-rate controller target |
| `min_burn` | TAO amount in rao | ✅ yes | burned-registration cost floor |
| `max_burn` | TAO amount in rao | ✅ yes | burned-registration cost ceiling |
| `bonds_moving_avg` | fraction (1,000,000 = 1.0) | ✅ yes | bonds EMA smoothing factor |
| `max_regs_per_block` | integer | sudo only | per-block registration cap |
| `serving_rate_limit` | blocks (12s) | ✅ yes | cooldown between axon serve calls |
| `max_validators` | integer | sudo only | top-stake validator permit cap |
| `adjustment_alpha` | fraction (u64, u64::MAX = 1.0) | ✅ yes | difficulty/burn adjust smoothing |
| `commit_reveal_period` | epochs (tempos) | ✅ yes | weight commit-to-reveal delay |
| `commit_reveal_weights_enabled` | flag | ✅ yes | commit-reveal weights toggle |
| `alpha_high` | fraction (u16, 65535 = 1.0) | ✅ yes | liquid-alpha smoothing upper bound |
| `alpha_low` | fraction (u16, 65535 = 1.0) | ✅ yes | liquid-alpha smoothing lower bound |
| `liquid_alpha_enabled` | flag | ✅ yes | per-weight bonds EMA (liquid alpha) |
| `bonds_penalty` | fraction (u16, 65535 = 1.0) | ✅ yes | penalty on out-of-consensus bonds |
| `alpha_sigmoid_steepness` | integer | ✅ yes | liquid-alpha sigmoid steepness |
| `min_childkey_take` | fraction (u16, 65535 = 1.0) | ✅ yes | floor for childkey take |
| `owner_immune_neuron_limit` | integer | ✅ yes | owner-designated prune-immune UIDs |
| `max_allowed_uids` | integer | ✅ yes | neuron slot capacity before pruning |
| `burn_increase_mult` | multiplier (U64F64 bits / 2^64) | ✅ yes | burn cost bump per registration |
| `burn_half_life` | blocks (12s) | ✅ yes | burn cost decay half-life |
| `collateral_lock_share` | fraction (u16, 65535 = 1.0) | ✅ yes | registration price share locked |
| `collateral_drain_ratio` | multiplier (U64F64 bits / 2^64) | ✅ yes | collateral released per α earned |
| `yuma3_enabled` | flag | ✅ yes | yuma3 consensus variant toggle |
| `yuma_version` | integer | sudo only | epoch consensus variant (2 or 3) |
| `subnet_is_active` | flag | sudo only | subnet started (staking + emissions) |
| `subnet_emission_enabled` | flag | sudo only | root switch for TAO emission share |
| `user_liquidity_enabled` | flag | sudo only | legacy user-LP flag (always false) |
| `bonds_reset_enabled` | flag | ✅ yes | bonds reset on metadata commit |
| `transfers_enabled` | flag | ✅ yes | stake transfers between coldkeys |
| `owner_cut_enabled` | flag | ✅ yes | owner emission cut toggle |
| `owner_cut_auto_lock_enabled` | flag | ✅ yes | auto-lock the owner's emission cut |

## Taostats

Each subnet tab lists pertinent hyperparameters:

<Image border={false} alt="Dark-themed subnet metagraph tab with a Settings & Metrics grid of hyperparameter label-value cards including UID counts, validator/miner counts, and epoch countdowns" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/ef79a494a17aa94b.png" />

The full list can be found at: [https://taostats.io/settings?subnet=19](https://taostats.io/settings?subnet=19) (update the subnet number for the specific subnet parameters)

## Using CLI

To see the parameters of a subnet, use the `btcli su get`**or** `btcli s hyperparameters`

Here are example parameters from Subnet 15 at the time of writing:

```
btcli s hyperparameters
Netuid: 19
                                                                           
                          Subnet Hyperparameters                           
                        NETUID: 19 - Network: finney                       
                                                                           
                                                                           
 HYPERPARAMETER                     VALUE                  NORMALIZED      
 ───────────────────────────────────────────────────────────────────────── 
   rho                              10                     10              
   kappa                            32767                  0.4999923705    
   immunity_period                  7000                   7000            
   min_allowed_weights              1                      1               
   max_weight_limit                 65535                  1               
   tempo                            360                    360             
   min_difficulty                   18446744073709551615   1               
   max_difficulty                   18446744073709551615   1               
   weights_version                  60000                  60000           
   weights_rate_limit               100                    100             
   adjustment_interval              360                    360             
   activity_cutoff                  20000                  20000           
   registration_allowed             True                   True            
   target_regs_per_interval         1                      1               
   min_burn                         100                    τ0.000000100    
   max_burn                         100000000000           τ100.000000000  
   bonds_moving_avg                 900000                 4.878909776e-14 
   max_regs_per_block               1                      1               
   serving_rate_limit               50                     50              
   max_validators                   64                     64              
   adjustment_alpha                 14757395258967642112   0.8             
   difficulty                       18446744073709551615   1               
   commit_reveal_weights_interval   1                      1               
   commit_reveal_weights_enabled    False                  False           
   alpha_high                       58982                  0.9000076295    
   alpha_low                        45875                  0.7000076295    
   liquid_alpha_enabled             False                  False           
 ───────────────────────────────────────────────────────────────────────── 
                                                  
```

* **rho**: 10 for all subnets.  [Rho](https://github.com/opentensor/bittensor/blob/0759f6a584a05e0d1dcbbf2baf54ae80b36e26cb/bittensor/subtensor.py#L2647_)  (p) is calculated based on the network's target inflation and actual neuron staking.  It adjusts the emission rate of the TAO token to balance the network's economy and dynamics. The formula for Rho is defined as: p = (Staking\_Target / Staking\_Actual) \* Inflation\_Target. Here, Staking\_Target and Staking\_Actual represent the desired and actual total stakes in the network,  while Inflation\_Target is the predefined inflation rate goal.
* **kappa**: 32767 for all subnets. [Kappa](https://github.com/opentensor/bittensor/blob/0759f6a584a05e0d1dcbbf2baf54ae80b36e26cb/bittensor/subtensor.py#L2661C13-L2665C115)  (κ) is used in the calculation of neuron ranks, which determine their share of network incentives. It is derived from the softmax function applied to the inter-neuronal weights set by each neuron. The formula for Kappa is: κ\_i = exp(w\_i) / Σ(exp(w\_j)), where w\_i represents the weight set by neuron i, and the denominator is the sum of exponential weights set by all neurons. This mechanism ensures a normalized and probabilistic distribution of ranks based on relative weights.
* **Immunity Period**: This parameter defines the duration during which new neurons are protected from certain network penalties or restrictions. (At 12 s/block, 1000 blocks is \~ 3.3 hours.)
* **Min Allowed Weights**: The minimum number of UIDs a subnet validator must set weights on, before the subnet validator is allowed to set weights on the blockchain.
* **Max Weight Limit**: Highest weight value that can be set by a validator.  This is a float value.
* **Tempo**: Cadence of updates, in blocks.
* **min\_difficulty / max\_difficulty / difficulty**: PoW registration difficulty floor, ceiling, and current value. Only relevant on subnets that allow proof-of-work registration (`network_pow_registration_allowed`); most subnets use burned registration instead.
* **weights version**: Sets the minimum version of validator code that a validator can use (and still set weights).
* **weights rate limit**: time (in blocks) that a validator may update weights.
* **adjustment\_interval**: Time (in blocks) after which the node registration cost is re-evaluated. If the number of actual registrations that occurred in the last `adjustment_interval` is higher than the [`target_regs_per_interval`](#target_regs_per_interval), then the blockchain will raise the recycle register cost, by increasing the [`min_burn`](#min_burn-max_burn) value by a certain amount, in order to slow down the actual registrations and bring them back to `target_regs_per_interval` value.
* **[activity cutoff](https://github.com/opentensor/developer-docs/blob/4d0319415d96462c1ffc48c76f2f9c913df5707e/docs/subnets/subnet-hyperparameters.md?plain=1#L219):**
  * Expressed in number of blocks. If a subnet validator has not set weights on the blockchain for `activity_cutoff` duration, then the Yuma Consensus will consider this subnet validator as offline, i.e., turned off. The weights of this subnet validator are considered too old to be useful. The weights of this subnet validator slowly lose their impact over time and eventually will no longer be considered for consensus calculation.
* **registration\_allowed**: When a subnet updates or there is an issue - the subnet owner may pause registrations to allow for all miners and validators to update their servers without the risk of deregistration.  When registration is turned off, emission to the subnet is recycled, and no participants receive emission.
* **target\_regs\_per\_interval**: Number of nodes that can be registered per epoch.  In the example above, just one node can be registered per interval.
* **min\_burn/max\_burn**: Node registration costs (in rao - 1e-9 tao).  The right column shows the value in tao.
* **serving\_rate\_limit**: Determines how often you can change your node's IP address on the blockchain. Expressed in number of blocks. Applies to both subnet validator and subnet miner nodes. Used when you move your node to a new machine.
* **[Bonds Moving Avg](https://github.com/opentensor/developer-docs/blob/4d0319415d96462c1ffc48c76f2f9c913df5707e/docs/subnets/subnet-hyperparameters.md?plain=1#L289)** :
  * This parameter controls how fast bonds will decay in the entire subnet. This is a unitless number. This number has a direct impact on subnet validator. The faster the bonds decay the quicker a subnet validator will lose its dividends after the subnet validator is out of the `activity_cutoff`.\
    If this `bonds_moving_avg` value is low, then the moving average of the bonds will decay slowly. This will allow the subnet validator to become active again, start setting new weights and start earning new bonds.\
    If this `bonds_moving_avg` value is high, then bonds in the subnet decay quickly. As a result, a subnet validator who has fallen out of the `activity_cutoff` and hence is running the risk of being viewed as "turned off", may not be able to become active again.
* **Max Validators**:  The number of validator slots available in the subnet.
* **Adjustment alpha:**  Larger numbers smooth the registration burn costs epoch to epoch.
* **Commit Reveal Period**: Weights are encrypted for this many epochs (tempos) before auto-reveal, to prevent [Weight Copying](/docs/weight-copying). (Formerly `commit_reveal_weights_interval`, measured in blocks.)
* **Commit Reveal Weights Enabled**: Boolean if commit reveal is on or off.
* **alpha\_high/alpha\_low**: used in Liquid alpha math. Not related to the alpha token
* **Liquid Alpha Enabled**: Liquid alpha allows for a Consensus based weights.
