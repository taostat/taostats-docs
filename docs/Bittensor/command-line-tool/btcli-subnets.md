---
title: 'CLI: Subnets'
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
Commands around subnets in the Bittensor command line tool.  

```
btcli s -h 
usage: btcli <command> <command args> subnets [-h] {list,metagraph,lock_cost,create,pow_register,register,hyperparameters} ...

positional arguments:
  {list,metagraph,lock_cost,create,pow_register,register,hyperparameters}
                        Commands for managing and viewing subnetworks.
    list                List all subnets on the network
    metagraph           View a subnet metagraph information.
    lock_cost           Return the lock cost to register a subnet
    create              Create a new bittensor subnetwork on this chain.
    pow_register        Register a wallet to a network using PoW.
    register            Register a wallet to a network.
    hyperparameters     View subnet hyperparameters
```

- [informational](#Informational) : These commands return data on a subnet.
- [Subnet owners](#subnet-owners): Useful for registering a subnet
- [Validators and Miners](#miners-and-validators): Register a neuron on a subnet

# Informational

## list

```
btcli subnets list
btcli s list
```

The subnet list command provides a high-level overview of the subnets:

- **N**: Neurons in use
- **MAX_N**: Total possible neuron count
- **Emission** (percentage of emission allocated to each subnet
- **Tempo**: Each subnet can set their own epoch length
- **Recycle**: cost to register a neuron.
- **POW**: No longer used
- **SUDO**: Hotkey that registered the subnet.

```
btcli subnets list
                                                 Subnets - finney                                                 
 NETUID   N    MAX_N   EMISSION  TEMPO  RECYCLE        POW       SUDO                                             
   0      64   64.00    0.00%     100   τ1.00000  4611686.02 T   5C4hrfjw9DjXZTzV3MwzrrAr9P1MJhSrvWGWqi1eSuyUpnhM 
   1     1024  1.02 K   6.70%     99    τ0.27631  1000000.00 T   5Hpd1smgd8tjQYqZ7tuXBxiC85LYivtKwpYAmoXvpJiJghfu 
   2     256   256.00   1.95%     360   τ1.34627    100.00 T     5HeQuPVRSZVE3LWdKx9q6upyCi53TjQ4a2S8mnJ5emyWFf5b 
   3     256   256.00   2.09%     360   τ0.09555  1000000.00 T   5FNBJf6xruFpKNxi7SoQQdedXUpC5nneSMJdzP5pZNpq35iA 
   4     256   256.00   5.08%     360   τ1.22699    100.00 T     5CXGPMnq9RCCLUEvp9G2iUuabw69TSFM155UVS1S4Zmusaxv 
   5     256   256.00   0.00%     360   τ0.00000  1000000.00 T   5HiveMEoWPmQmBAb8v63bKPcFhgTGCmST1TVZNvPHSTKFLCv 
   6     209   256.00   3.70%     360   τ0.00000  18446744.07 T  5H6VnWCi8wDV5xfatGtAbjkqiCtGoet7euCQNJTVjkL4LQcM 
   <snip>
```

## metagraph

Retrieve the Metagraph of a subnet: `btcli subnets metagraph`. You'll then be prompted for the subnet that you wish to query.  The output will be all the data for every node on the subnet.  This is what the [Taostats Home](doc:taostats-home) metagraph is built with.

```
btcli subnets metagraph
Enter netuid [0/1/2/3/4/5/6/7/8/9/10/11/12/13/14/15/16/17/18/19/20/21/22/23/24/25/26/27/28/29/30/31/32] (0): 18
📡 Syncing with chain: finney ...
   Metagraph: net: finney:18, block: 2397787, N: 27/256, stake: τ5,164,685.825409024, issuance: τ7,092,985.980079588, difficulty: 18446744073709551615    
UID        STAKE(τ)     RANK      TRUST  CONSENSUS  INCENTIVE  DIVIDENDS   EMISSION(ρ)    VTRUST  VAL  UPDATED  ACTIVE  AXON                   HOT…  COLD…
0      642754.68750  0.00000    0.00000    0.00000    0.00000    0.13381    1649700992   0.97478    *      689       1  64.227.114.35:8091     5Hd…  5DCQ…
1      285578.53125  0.00000    0.00000    0.00000    0.00000    0.05753     709426816   0.97719    *       53       1  none                   5Dv…  5DkZ…
2           4.58063  0.00414    0.95227    0.00412    0.00414    0.00000      51148100   0.18521    *   164379       0  213.173.107.105:11550  5Dk…  5E7A…
<snip>
```

## [hyperparameters](doc:subnet-parameters)

Obtain details on a particular subnet:

```
btcli subnets hyperparameters
Enter netuid [0/1/2/3/4/5/6/7/8/9/10/11/12/13/14/15/16/17/18/19/20/21/22/23/24/25/26/27/28/29/30/31/32] (0): 18
   Subnet Hyperparameters - NETUID: 18 - finney   
 HYPERPARAMETER              VALUE                
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
   adjustment_alpha          58000
   difficulty                18446744073709551615 
```

# Subnet owners

## Subnet Lock cost

This endpoint tells you the current cost in tao to register a Subnet:

```
>btcli subnets lock_cost
Subnet lock cost: τ165.847224408

```

## Create

Steps to create a new subnet.

# Miners and Validators

## Register

Register a neuron on the subnet.  Use this command to create a miner or validator on a subnet.  Provide your wallet and hotkey to register.

```
btcli s register
Enter subtensor network [local/finney/test/archive] (finney): 
Enter netuid [0/1/2/3/4/5/6/7/8/9/10/11/12/13/14/15/16/17/18/19/20/21/22/23/24/25/26/27/28/29/30/31/32] (0): 18
Enter wallet name (default): 
<snip>
```

# Deprecated Commands

## pow register

#