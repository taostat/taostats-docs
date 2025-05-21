---
title: Staking Instructions
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
A few assumptions.  You have a 

- wallet (or coldkey)
- the wallet has tao in it.

> 📘 One stake event every 360 blocks
> 
> You make stake or unstake to a validator hotkey once every 360 blocks.  So a 2nd stake, or an unstake must wait about 72 minutes.
> 
> You can unstake from validator1, and immediately stake to validator2 since these are two different hotkeys.

# btcli

If you have the Bittensor command line tool installed.

```
btcli root delegate
```

![](https://files.readme.io/305a0e046c84fc0e699da805d75b73389b9603dd69714f0411ff4029cf968da0-image.png)

Choose the number of the validator you wish to delegate to. we chose 1 for taostats)

```
Enter delegate index: 1
Enter wallet name (default):<walletname>
Stake all Tao from account: 'walletname'? [y/n]:n
Enter Tao amount to stake: 1
Do you want to delegate:
  amount: τ0.999999000
  to: 5GKH9FPPnWSUoeeTJp19wVtd84XqFW4pyK2ijV2GsFbhTrP1
 owner: 5GcCZ2BPXBjgG88tXJCEtkbdg2hNrPbL4EFfbiVRvBZdSQDC [y/n]: 
 
```

<br />

# taostats (using Polkadot wallet)

If you have a wallet that has a Chrome extension, you can delegate and undelgate from your browser using taostats. The instructions below show the polkadot wallet, but all wallets should be similar.

1. Connect your wallet. Choose the wallets you wish to connect
2. ![](https://files.readme.io/ebee3e4f1a5ea5a56bc8ae189154979b7b61ef808251d3ce4035f4aaff5ec7c9-image.png)

   ![](https://files.readme.io/50153c8cb90638ba8a84869a7fb8cf1af387c6d4c26c0ecec74012a97e1c8ba5-image.png)

   The tool will show your available balance and a list of validators. Add the amount of tao, and the validator, anc Click Delegate.
3. The wallet exension willl ask for your password.
4. ![](https://files.readme.io/40f6da244b32de30c67d9356bcafdfe48e2b61d6c25403cfd6fc0ffa78d0b2b3-image.png)

![](https://files.readme.io/38fc6452dfcabed3190a4e09fb9c52dbae49130e95ad9c3ce71cb139da66c392-image.png)