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

# Neuron Registration

To obtain a UID (unique slot number for a neuron) on a particular subnet you must register your hotkey.  The cost of the slot is variable and can be found using the command line `btcli subnets list`. The **recycle** cost is the cost to register a neuron).  

The number of registrations per epoch is defined in the subnet parameters (default: 3) and if all three slots are registered in a given epoch the cost will increase for the next epoch. If some but not all slots are filled the costs will remain the same for the next epoch. If none of the slots are registered then the cost for the next epoch will decrease.

This allows the registration costs to be defined by natural market forces of demand. A historical chart is available on the subnet's page on Taostats to see the current costs for each subnet:

<Image alt="URL format: <https://taostats.io/subnets/netuid-18/#registration>" align="center" src="https://files.readme.io/de95227252701b51d1a1ef968be37bc5a09b642ccdce095f3b3253ef58fe55ca-Screenshot_2024-09-03_at_17.40.57.jpg">
  URL format: [https://taostats.io/subnets/netuid-18/#registration](https://taostats.io/subnets/netuid-18/#registration)
</Image>

All new miners & validators are placed into <Glossary>immunity</Glossary> for a preset amount of time.  The immunity period can be adjusted per subnet.  A miner with immunity cannot be de-registered.

> 👍 Immunity period
>
> To retrieve the immunity period (in blocks), you can use the [Bittensor CLI](doc:command-line-tool) to select a Subnet. The output includes the immunity\_period.  For subnet 1, it is 7200 blocks:
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

Any tao spent on registration is recycled - it is returned to the unissued supply (thus slowly lengthening the time until the next halvening). The tao recycled for registration is NOT returned to the miner upon de-registration and is considered part of the operational costs to be factored into the profitability calculations when mining. 

## Registration Cost

Registration cost is based on the demand, the more registrations, the higher the cost.  In the parameters above, the min/max burn denotes the range of the registration cost in 1e-9 tao (rao). 

# Neuron De-registration

When a new miner/validator registers their hotkey, the neuron/node with the lowest emissions ranking in the subnet is de-registered.

> 📘 Miners & validators that have immunity cannot be de-registered.

If your subnet is deregistered for a new subnet, all neurons are de-registered.
