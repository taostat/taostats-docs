---
title: 'CLI: Config'
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
Configure the CLI with defaults for your usage

# get

Prints the current configuration

The default configuration:

```
  Name             Value                           
 ───────────────────────────────────────────────── 
  wallet_name      None                            
  wallet_path      None                            
  wallet_hotkey    None                            
  network          None (default = finney)         
  chain            None                            
  use_cache        True                            
  metagraph_cols   ACTIVE                    True  
                   AXON                      True  
                   COLDKEY                   True  
                   CONSENSUS                 True  
                   DIVIDENDS                 True  
                   EMISSION                  True  
                   HOTKEY                    True  
                   INCENTIVE                 True  
                   RANK                      True  
                   STAKE                     True  
                   TRUST                     True  
                   UID                       True  
                   UPDATED                   True  
                   VAL                       True  
                   VTRUST                    True  
                                                    
```

# clear

Clears the current configuration

# metagraph

Configure the columns that appear when calling `btcli subnet metagraph`

<Image alt="In this example axon and Active are disabled." align="center" src="https://files.readme.io/11e11623030bb381627db9395475c14d4b471a20146222a4fc600b15a73adb96-image.png">
  In this example axon and Active are disabled.
</Image>

# set

Set your defaults

![](https://files.readme.io/269c3ea72ea3bb08aabb5a4d04a934146aacc2e640562a9c1d8cf96b5a33b3d9-image.png)
