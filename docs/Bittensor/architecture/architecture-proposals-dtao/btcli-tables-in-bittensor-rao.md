---
title: btcli tables in Bittensor Rao
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
When changing the emissions protocol, you can expect huge changes in the charts we have grown used to interact with.  Here are some pointers to using the new btcli commands.

# btcli stake add

the `delegate` commands are no longer used.  All commands are run through the stake add (remove/move) commands.

Let's add stake to a hotkey registered on subnet 2:

The chart shows you the hotkey, how much, conversion rate, your received alpha (beta) and the slippage:

```
$ btcli st add   --subtensor.network local 

Enter netuid (0): 2
Enter wallet name (default): dtao
Enter staking hotkey name or ss58_address (default): 5DNnU3JjWVcXT28wBvbsK9ihJjSgkugU5ayin8fh5LaZBLy5
Stake all: τ1,999.3250? [y/n]: y
                                               Add Stake: 5HbjWim3NhYzGvacnZPL46tTLV5Sv5CrTKmis8aWTvhJbBLp                                               
    netuid     ┃       hotkey       ┃       amount (τ)       ┃                 rate (β/τ)                  ┃      received (β)       ┃     slippage      
━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━
       2       │     5DN...Ly5      │      τ1,999.3250       │           1.8872974366492192(β/τ)           │       2,639.5357β‎       │     30.0474 %     
───────────────┼────────────────────┼────────────────────────┼─────────────────────────────────────────────┼─────────────────────────┼───────────────────
               │                    │                        │                                             │                         │                   
        -------------------------------------------------------------------------------------------------------------------
        WARNING:        Slippage is high: 30.0474 %, this may result in a loss of funds. 
        -------------------------------------------------------------------------------------------------------------------

```

# btcli stake move

Move your staked tao from from subnet/hotkey to another subnet/hotkey.

- Move stake in the same subnet - and swap hotkeys. This will incur zero slippage as you are in the same subnet)

```
btcli st move 
Enter origin netuid (0): 2
Enter destination netuid (0): 2
Enter coldkey name (default): rao
Enter origin hotkey name or ss58_address (default): 5FcDHCx5KpAX1ECqGuPZXGRHj8hAwjej7Hwh4roWy2HvCrHe
Enter destination hotkey name or ss58_address (default): 5DoFxQgKZopsyKGTuYt2M5baRZAjcjeCUDSdpZDi7JrMowxL
Move all: 1.1217 β‎? [y/n]: y
                                                                                                                                         Move Stake                                                                                                                                         
             origin netuid              ┃             origin hotkey              ┃            dest netuid            ┃           dest hotkey            ┃           amount (β)           ┃           rate  (β/β)            ┃            recieved (β)             ┃        slippage         
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━
                  β(2)                  │               5Fc...rHe                │               β(2)                │            5Do...wxL             │            1.1217 β‎            │              1.0β/β              │              1.1217 β‎               │           0%            
────────────────────────────────────────┼────────────────────────────────────────┼───────────────────────────────────┼──────────────────────────────────┼────────────────────────────────┼──────────────────────────────────┼─────────────────────────────────────┼─────────────────────────
                                        │                                        │                                   │                                  │                                │                                  │                                     │                         


```

- Move stake across subnets - to the same hotkey, or a different one. Moving alpha stake across subnets will incur a slippage.

```
btcli st move
Enter origin netuid (0): 1
Enter destination netuid (0): 2
Enter coldkey name (default): rao
Enter origin hotkey name or ss58_address (default): 5FbfQ61pKLaVAJ8rR2p2B6ioJw6LNpcYgdKuCij6x1dnKoNT
Enter destination hotkey name or ss58_address (default): 5FbfQ61pKLaVAJ8rR2p2B6ioJw6LNpcYgdKuCij6x1dnKoNT
Move all: 116.0991 α‎? [y/n]: y
                                                                                                                                         Move Stake                                                                                                                                         
           origin netuid            ┃           origin hotkey            ┃          dest netuid          ┃          dest hotkey          ┃         amount (α)          ┃                       rate  (β/α)                       ┃           recieved (β)           ┃       slippage        
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━
                α(1)                │             5Fb...oNT              │             β(2)              │           5Fb...oNT           │         116.0991 α‎          │                 0.36601241403859214β/α                  │            42.1347 β‎             │       0.2462 %        
────────────────────────────────────┼────────────────────────────────────┼───────────────────────────────┼───────────────────────────────┼─────────────────────────────┼─────────────────────────────────────────────────────────┼──────────────────────────────────┼───────────────────────
                                    │                                    │                               │                               │                             │                                                         │                                  │                       
                                    
```

# btcli subnet list

This lists all of the subnets, their emission, and information about the token and conversion to tao.

```
                                                                                                                                            Subnets - rao                                                                                                                                             
                                                                                                                                                                                                                                                                                                      
           Netuid           ┃           Symbol           ┃                                   Emission (τ) ┃                                         TAO(τ) ┃                                          Stake(α) ┃               Rate (α/τ)                ┃                Tempo (k/n)                 
━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
             0              │             τ              │                                       τ 0.0000 │                                     τ 579.0260 │                                        579.0260 τ │               1.0000 τ/τ                │                   38/100                   
             2              │             β              │                                       τ 0.2245 │                                   τ 5,037.4243 │                                     15,364.2237 β │               0.2922 τ/β                │                  314/441                   
             8              │             θ              │                                       τ 0.1033 │                                   τ 2,318.5485 │                                     14,795.0593 θ │               0.1320 τ/θ                │                  275/958                   
             12             │             μ              │                                       τ 0.0963 │                                   τ 2,160.2676 │                                     13,792.1730 μ │               0.1670 τ/μ                │                  30/1028                   
             1              │             α              │                                       τ 0.0923 │                                   τ 2,071.5843 │                                     12,568.0831 α │               0.1070 τ/α                │                  360/1072                  
             10             │             κ              │                                       τ 0.0626 │                                   τ 1,404.4772 │                                     12,855.8705 κ │               0.0802 τ/κ                │                  707/1200                  
             9              │             ι              │                                       τ 0.0618 │                                   τ 1,386.5258 │                                     15,523.5555 ι │               0.0844 τ/ι                │                  706/1200                  
             7              │             η              │                                       τ 0.0555 │                                   τ 1,244.8638 │                                     14,486.7022 η │               0.0690 τ/η                │                  704/1200                  
             6              │             ζ              │                                       τ 0.0508 │                                   τ 1,140.7683 │                                     14,867.5373 ζ │               0.0645 τ/ζ                │                  703/1200                  
             3              │             γ              │                                       τ 0.0418 │                                     τ 938.0996 │                                     16,181.6471 γ │               0.0571 τ/γ                │                  700/1200                  
             5              │             ε              │                                       τ 0.0336 │                                     τ 753.4745 │                                     16,796.2056 ε │               0.0477 τ/ε                │                  702/1200                  
             4              │             δ              │                                       τ 0.0319 │                                     τ 716.1923 │                                     16,838.4833 δ │               0.0454 τ/δ                │                  701/1200                  
             13             │             ν              │                                       τ 0.0308 │                                     τ 691.3259 │                                     12,117.5937 ν │               0.0554 τ/ν                │                  710/1200                  
             11             │             λ              │                                       τ 0.0253 │                                     τ 567.6519 │                                     14,166.3862 λ │               0.0440 τ/λ                │                  708/1200                  
             16             │             π              │                                       τ 0.0177 │                                     τ 396.6541 │                                      9,823.8763 π │               0.0593 τ/π                │                  713/1200                  
             14             │             ξ              │                                       τ 0.0154 │                                     τ 345.9552 │                                     10,522.4218 ξ │               0.0315 τ/ξ                │                  711/1200                  
             15             │             ο              │                                       τ 0.0123 │                                     τ 275.5102 │                                      9,921.6595 ο │               0.0290 τ/ο                │                  712/1200                             τ 36.4267 │                                      4,463.7029 φ │               0.0132 τ/φ                │                  718/1200                  
────────────────────────────┼────────────────────────────┼────────────────────────────────────────────────┼────────────────────────────────────────────────┼───────────────────────────────────────────────────┼─────────────────────────────────────────┼────────────────────────────────────────────
                            │                            │                                                │                                                │                                                   │                                         │                                            



```

- **Netuid**:  The Subnet number
- **Symbol**: Greek (hebrew, etc.) character representing the Subnet.
- **Emission**:  Breakdown of tao emission across subnets. This is determined by the amount of tao staked to the subnet.  This is represented as a fraction of tao. 
- **TAO(τ)**: tao staked to the subnet.
- **Stake(⍺)**: Amount of alpha token available. This is direct conversion of P(τ.
- **Rate: (⍺, τ)**: Conversion rate from the alpha into tao. Or tao/alpha from the last 2 columns.
- **Tempo**:  Tempo varies by how much tao is staked to the subnet.

# btcli subnet show

```
                Subnet: 2: Owner: 5HbjWim3NhYzGvacnZPL46tTLV5Sv5CrTKmis8aWTvhJbBLp, Total Locked: 206.1464β‎, Owner Locked: 206.1464β‎




   Index   ┃   Symbol   ┃    Emission (τ)     ┃                     P(τ, ┃ α)                    ┃         α          ┃    Rate (α/τ)    ┃   Tempo    
━━━━━━━━━━━╇━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━
     2     │     β      │       τ0.3623       │          P( τ2,662.2423, │ 3,285.5701β )         │    4,778.4299β     │    0.8103τ/β     │  129/273   




                                                                   Subnet State #2                                                                    
 uid  ┃       β       ┃   Global(τ)   ┃  stake   ┃  dividends  ┃  incentive  ┃  emission (β)  ┃                        hotkey                         
━━━━━━╇━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━╇━━━━━━━━━━╇━━━━━━━━━━━━━╇━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  0   │  3,753.1826β‎  │  τ6,456.3339  │  1.0000  │     0.0     │     0.0     │    1.0000β‎     │   5ETnYbd1asLmArmPQwcKzQGSzPLKB5fN4AcCXm5ZXX11GDcG    
──────┼───────────────┼───────────────┼──────────┼─────────────┼─────────────┼────────────────┼───────────────────────────────────────────────────────
      │               │               │          │             │             │                │                                                       
```

**Top row** hows the subnet owner's key, and how much tao the owner has locked to this subnet.  Locked alpha ensures this key retains ownership.

**Top chart**:

This replicates the data from `btcli subnet list` but just for this subnet

**Main Chart**

This is similar to the current btcli metagraph - showing all of the neurons registered to the subnet.  Notice in the example above, that the subnet owner gains UID 0 by default.

We can see the amount of token (beta, in this case).  As there is just one UID, all emission goes to this uid. Adding a second UID, we see emission is divided based on the staked amounts:

```
                                                                     Subnet State #2                                                                     
 uid  ┃       β        ┃    Global(τ)    ┃  stake   ┃  dividends  ┃  incentive  ┃  emission (β)  ┃                        hotkey                         
━━━━━━╇━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━╇━━━━━━━━━━╇━━━━━━━━━━━━━╇━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  0   │  9,574.5228β‎   │  τ12,931.1954   │  0.8438  │     0.0     │     0.0     │    0.8439β‎     │   5ETnYbd1asLmArmPQwcKzQGSzPLKB5fN4AcCXm5ZXX11GDcG    
  1   │  2,643.7618β‎   │   τ1,371.9084   │  0.1561  │     0.0     │     0.0     │    0.1561β‎     │   5DNnU3JjWVcXT28wBvbsK9ihJjSgkugU5ayin8fh5LaZBLy5    
──────┼────────────────┼─────────────────┼──────────┼─────────────┼─────────────┼────────────────┼───────────────────────────────────────────────────────
      │                │                 │          │             │             │                │                                               
```

# btcli stake list

```
                                            hotkey: 5FbfQ61pKLaVAJ8rR2p2B6ioJw6LNpcYgdKuCij6x1dnKoNT                                             
                                                                                                                                                 
 Netuid  ┃ Symbol ┃     TAO(τ) ┃    Stake(α) ┃  Rate(τ/α)  ┃  Value(α x τ/α) ┃        Swap(α) -> τ ┃  Registered ┃ Emission(α/block) ┃ Locked(α) 
━━━━━━━━━╇━━━━━━━━╇━━━━━━━━━━━━╇━━━━━━━━━━━━━╇━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━
 1       │      α‎ │  τ 24.0240 │  157.4016 α │ 0.1013 τ/α  │       τ 15.9406 │  τ 15.8283 (0.704%) │         YES │          0.0073 α‎ │  0.0000 α‎ 
 2       │      β‎ │   τ 8.9870 │   28.7272 β │ 0.2805 τ/β  │        τ 8.0588 │   τ 8.0471 (0.145%) │         YES │          0.0021 β‎ │  0.0000 β‎ 
 3       │      γ‎ │   τ 2.0264 │   35.2100 γ │ 0.0602 τ/γ  │        τ 2.1187 │   τ 2.1146 (0.194%) │         YES │          0.0021 γ‎ │  0.0000 γ‎ 
 4       │      δ‎ │   τ 1.1637 │   27.5335 δ │ 0.0434 τ/δ  │        τ 1.1941 │   τ 1.1923 (0.151%) │         YES │          0.0018 δ‎ │  0.0000 δ‎ 
 5       │      ε‎ │   τ 1.4583 │   32.6697 ε │ 0.0456 τ/ε  │        τ 1.4886 │   τ 1.4860 (0.179%) │         YES │          0.0020 ε‎ │  0.0000 ε‎ 
 6       │      ζ‎ │   τ 2.4118 │   32.0925 ζ │ 0.0626 τ/ζ  │        τ 2.0079 │   τ 2.0047 (0.159%) │         YES │          0.0021 ζ‎ │  0.0000 ζ‎ 
 7       │      η‎ │   τ 3.0167 │   36.0081 η │ 0.0671 τ/η  │        τ 2.4151 │   τ 2.4109 (0.175%) │         YES │          0.0022 η‎ │  0.0000 η‎ 
 8       │      θ‎ │   τ 3.9587 │   26.4221 θ │ 0.1293 τ/θ  │        τ 3.4164 │   τ 3.4119 (0.132%) │         YES │          0.0018 θ‎ │  0.0000 θ‎ 
 9       │      ι‎ │   τ 7.1767 │   81.0266 ι │ 0.0812 τ/ι  │        τ 6.5785 │   τ 6.5504 (0.427%) │         YES │          0.0025 ι‎ │  0.0000 ι‎ 
─────────┼────────┼────────────┼─────────────┼─────────────┼─────────────────┼─────────────────────┼─────────────┼───────────────────┼───────────
         │        │  τ 54.2232 │             │             │       τ 43.2188 │                     │             │                   │           
```

- **TAO**: amount of tao staked
- **Stake** amount of alpha taked
- **Rate τ/⍺**: Exchange rate tao/alpha
- ** Value**: Conversion of alpha to tao
- ** Swap Conversion**: How much alpha-> tao will return (this includes slippage).
- **Regitered**:Is this Hotkey registered on the Subnet
- **Emission** Emission per block for this hotkey
- **Locked** Amount of take that i locked