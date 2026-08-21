---
title: Neuron Registration
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

Neurons are server nodes in each subnet.  To become a validator or miner on a subnet you must register a neuron.

To obtain a UID (unique slot number for a neuron) on a particular subnet you must register your hotkey.  The cost of the slot is variable and can be found using the command line `btcli subnets list`. The **recycle** cost is the cost to register a neuron).

The recycle cost decays smoothly each block, ensuring the price halves from the last registration cost every half life blocks.
At each registration the recycle cost is increased by a multiplier Burn Increase Multiplier (clamped between limits).
It is possible to register multiple neurons per block

This allows the registration costs to be defined by natural market forces of demand. A historical chart is available on the subnet's page on Taostats to see the current costs for each subnet:

<Image border={false} alt="URL format: https://taostats.io/subnets/netuid-18/#registration" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/d47a20ae66b744b0.jpg" />

All new miners & validators are placed into [immunity](/docs/glossary#immunity) for a preset amount of time.  The immunity period can be adjusted per subnet.  A miner with immunity cannot be de-registered.

> 📘 **Immunity period**
>
> To retrieve the immunity period (in blocks), you can use the [Bittensor CLI](/docs/command-line-tool) to select a Subnet. The output includes the immunity\_period.  For subnet 1, it is 7200 blocks:
>
> ```
> btcli sudo get
> Enter netuid [0/1/2/3/4/5/6/7/8/9/10/11/12/13/14/15/16/17/18/19/20/21/22/23/24/25/26/27/28/29/30/31/32] (0): 1
> Bittensor Version: Current 6.6.0/Latest 6.7.0
> Please update to the latest version at your earliest convenience. Run the following command to upgrade:
>
> python -m pip install --upgrade bittensor
>   Subnet Hyperparameters - NETUID: 1 - finney  
>  HYPERPARAMETER            VALUE               
>  rho                       10                  
>  kappa                     32767               
>  immunity_period           7200                
>  min_allowed_weights       8                   
>  max_weight_limit          455                 
>  tempo                     99                  
>  min_difficulty            1000000000000000000 
>  max_difficulty            1000000000000000000 
>  weights_version           10000               
>  weights_rate_limit        100                 
>  adjustment_interval       112                 
>  activity_cutoff           5000                
>  registration_allowed      True                
>  target_regs_per_interval  2                   
>  min_burn                  50000000            
>  max_burn                  100000000000        
>  bonds_moving_avg          900000              
>  max_regs_per_block        1                   
>  serving_rate_limit        10                  
>  max_validators            128         
> ```

## Recycling of Fees

Any tao spent on registration is converted into alpha and [recycled](/docs/recycling) - it is returned to the unissued supply (thus slowly lengthening the time until the next halvening). The tao recycled for registration is NOT returned to the miner upon de-registration and is considered part of the operational costs to be factored into the profitability calculations when mining.

> 📘 **Some subnets add a collateral lock on top of the recycle**
>
> On subnets that enable **miner collateral**, the registration cost is *split*: the recycled share behaves exactly as above (converted to alpha, removed from supply), but a second share — set by the subnet's `CollateralLockShare` (up to 95%) — is staked to your hotkey and **frozen as a bond** instead of being burned. You recover that locked alpha only by earning emission (it drains back to free stake as you mine), or if the subnet dissolves. It is off by default and opt-in per subnet, so most registrations are recycle-only — but if you register on a collateral subnet, budget for the extra locked capital. See [Miner collateral](/docs/miner-collateral) for the full mechanics.

# Neuron De-registration

When a new miner/validator registers their hotkey, the neuron/node with the lowest emissions ranking in the subnet is de-registered.

> 📘 **Miners & validators that have immunity cannot be de-registered.**

If your subnet is deregistered for a new subnet, all neurons are de-registered.
