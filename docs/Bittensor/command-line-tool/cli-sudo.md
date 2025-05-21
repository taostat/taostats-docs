---
title: 'CLI: Sudo'
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
The sudo commands are generally just of interest to subnet owners

```
 btcli sudo  --help
                                                                                                                                                                       
 Usage: btcli sudo [OPTIONS] COMMAND [ARGS]...                                                                                                                         
                                                                                                                                                                       
╭─ Options ───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ --help          Show this message and exit.                                                                                                                         │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
╭─ Subnet Configuration ──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ get   Shows a list of the hyperparameters for the specified subnet.                                                                                                 │
│ set   Used to set hyperparameters for a specific subnet.                                                                                                            │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
                                                                                                                                                                       
 Made with ❤ by The Openτensor Foundaτion                 
```

# set

Set hyperparameters for a subnet.

# get

Gets the hyperparameters for a subnet.

```
btcli sudo get
Enter netuid [0/1/2/3/4/5/6/7/8/9/10/11/12/13/14/15/16/17/18/19/20/21/22/23/24/25/26/27/28/29/30/31/32] (0): 18
  Subnet Hyperparameters - NETUID: 18 - finney  
 HYPERPARAMETER            VALUE                
 rho                       10                   
 kappa                     32767                
 immunity_period           5000                 
 min_allowed_weights       1                    
 max_weight_limit          65535                
 tempo                     360                  
 min_difficulty            18446744073709551615 
 max_difficulty            18446744073709551615 
 weights_version           0                    
 weights_rate_limit        100                  
 adjustment_interval       360                  
 activity_cutoff           5000                 
 registration_allowed      True                 
 target_regs_per_interval  2                    
 min_burn                  1000000000           
 max_burn                  100000000000         
 bonds_moving_avg          900000               
 max_regs_per_block        1                    
 serving_rate_limit        5                    
 max_validators            64                   

```