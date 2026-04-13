---
title: Subnet Hyperparameters
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

## Taostats

Each subnet tab lists pertinent hyperparameters:

![](https://files.readme.io/bb83bb2b373645746c12a80ecdd871d349036ed4a284a861f6b13f53f0840e5c-image.png)

The full list can be found at: https://taostats.io/settings?subnet=19 (update the subnet number for the specific subnet parameters)

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

# Hyperparameter descriptions

* **rho**: 10 for all subnets.  [Rho](https://github.com/opentensor/bittensor/blob/0759f6a584a05e0d1dcbbf2baf54ae80b36e26cb/bittensor/subtensor.py#L2647_)  (p) is calculated based on the network's target inflation and actual neuron staking.  It adjusts the emission rate of the TAO token to balance the network's economy and dynamics. The formula for Rho is defined as: p = (Staking_Target / Staking_Actual) * Inflation_Target. Here, Staking_Target and Staking_Actual represent the desired and actual total stakes in the network,  while Inflation_Target is the predefined inflation rate goal.
* **kappa**: 32767 for all subnets. [Kappa](https://github.com/opentensor/bittensor/blob/0759f6a584a05e0d1dcbbf2baf54ae80b36e26cb/bittensor/subtensor.py#L2661C13-L2665C115)  (κ) is used in the calculation of neuron ranks, which determine their share of network incentives. It is derived from the softmax function applied to the inter-neuronal weights set by each neuron. The formula for Kappa is: κ_i = exp(w_i) / Σ(exp(w_j)), where w_i represents the weight set by neuron i, and the denominator is the sum of exponential weights set by all neurons. This mechanism ensures a normalized and probabilistic distribution of ranks based on relative weights.
* **Immunity Period**: This parameter defines the duration during which new neurons are protected from certain network penalties or restrictions. (At 12 s/block, 1000 blocks is ~ 3.3 hours.)
* **Min Allowed Weights**: The minimum number of UIDs a subnet validator must set weights on, before the subnet validator is allowed to set weights on the blockhain.
* **Max Weight Limit**: Highest weight value that can be set by a validator.  This is a float value.
* **Tempo**: Cadence of updates, in blocks.
* **min_difficulty**: Obsolete - no longer used.
* **max_difficulty**: Obsolete - no longer used.
* **weights version**: Sets the minimum version of validator code that a validator can use (and still set weights).
* **weights rate limit**: time (in blocks) that a validator may update weights.
* **adjustment_interval**: Time (in blocks) after which the node registration cost is re-evaluated. If the number of actual registrations that occurred in the last `adjustment_interval` is higher than the [`target_regs_per_interval`](#target_regs_per_interval), then the blockchain will raise the recycle register cost, by increasing the [`min_burn`](#min_burn-max_burn) value by a certain amount, in order to slow down the actual registrations and bring them back to `target_regs_per_interval` value.
* **[activity cutoff](https://github.com/opentensor/developer-docs/blob/4d0319415d96462c1ffc48c76f2f9c913df5707e/docs/subnets/subnet-hyperparameters.md?plain=1#L219):**
  * Expressed in number of blocks. If a subnet validator has not set weights on the blockchain for `activity_cutoff` duration, then the Yuma Consensus will consider this subnet validator as offline, i.e., turned off. The weights of this subnet validator are considered too old to be useful. The weights of this subnet validator slowly lose their impact over time and eventually will no longer be considered for consensus calculation.
* **registration_allowed**: When a subnet updates or there is an issue - the subnet owner may pause registrations to allow for all miners and validators to update their servers without the risk of deregistration.  When registration is turned off, emission to the subnet is recycled, and no participants receive emission.
* **target_regs_per_interval**: Number of nodes that can be registered per epoch.  In the example above, just one node can be registered per interval.
* **min_burn/max_burn**: Node registration costs (in rao - 1e-9 tao).  The right column shows the value in tao.
* **serving_rate_limit**: Determines how often you can change your node's IP address on the blockchain. Expressed in number of blocks. Applies to both subnet validator and subnet miner nodes. Used when you move your node to a new machine.
* **[Bonds Moving Avg](https://github.com/opentensor/developer-docs/blob/4d0319415d96462c1ffc48c76f2f9c913df5707e/docs/subnets/subnet-hyperparameters.md?plain=1#L289)** :
  * This parameter controls how fast bonds will decay in the entire subnet. This is a unitless number. This number has a direct impact on subnet validator. The faster the bonds decay the quicker a subnet validator will lose its dividends after the subnet validator is out of the `activity_cutoff`.  
    If this `bonds_moving_avg` value is low, then the moving average of the bonds will decay slowly. This will allow the subnet validator to become active again, start setting new weights and start earning new bonds.  
    If this `bonds_moving_avg` value is high, then bonds in the subnet decay quickly. As a result, a subnet validator who has fallen out of the `activity_cutoff` and hence is running the risk of being viewed as "turned off", may not be able to become active again.
* **Max Validators**:  The number of validator slots available in the subnet.
* **Adjustment alpha:**  Larger numbers smooth the registration burn costs epoch to epoch.
* **difficulty** No longer used
* **Commit Reveal Weights Interval**: Weights are encrypted for this many blocks (to prevent [Weight Copying](doc:weight-copying)).
* **Commit Reveal Weights Enabled**: Boolean if commit reveal is on or off.
* **alpha_high/alpha_low**: used in Liquid alpha math.
* **Liquid Alpha Enabled**: Liquid alpha allows for a Consensus based weights.
