---
title: 'CLI: Stake'
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
> 📘 Note: To perform an initial delegation of stake, use:
>
> ```
> btcli root delegate
> ```
>
>  [CLI: Root](doc:cli-root)

```
 btcli st --help
                                                                                                                                                                       
 Usage: btcli st [OPTIONS] COMMAND [ARGS]...                                                                                                                           
                                                                                                                                                                       
╭─ Options ───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ --help          Show this message and exit.                                                                                                                         │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
╭─ Stake Management ──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ add      Stake TAO to one or more hotkeys associated with the user's coldkey.                                                                                       │
│ remove   Unstake TAO from one or more hotkeys and transfer them back to the user's coldkey.                                                                         │
│ show     Lists all the stake accounts associated with a user's wallet.                                                                                              │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
╭─ Child Hotkeys ─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ child    Child Hotkey commands, alias: `children`                                                                                                                   │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
                                                                                                                                                                       
 Made with ❤ by The Openτensor Foundaτion                    
```

# Manage your stake

<br />

# add

 Stake TAO to one or more hotkeys associated with the user's coldkey.\
 This command is used by a subnet validator to stake to their own hotkey. Compare this command with "btcli root delegate" that is typically run by a TAO holder to\
 delegate their TAO to a delegate's hotkey.

> 📘 Note: the Validator hotkey must already be associated with your coldkey for this to add stake.
>
> For the initial staking process use:
>
> ```
> btcli root delegate-stake
> ```

#

## show

```
btcli stake show
Enter wallet name (default):
```

Enter your wallet name to display all of the hotkeys that have tao delegated to them.  This will include all active validators and miners.

<br />

# remove

Remove stake from a hotkey
