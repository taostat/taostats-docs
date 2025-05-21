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
```
btcli stake -h  
usage: btcli <command> <command args> stake [-h] {show,add,remove} ...

positional arguments:
  {show,add,remove}  Commands for staking and removing stake from hotkey accounts.
    show             List all stake accounts for wallet.
    add              Add stake to your hotkey accounts from your coldkey.
    remove           Remove stake from the specified hotkey into the coldkey balance.
```

# show

```
btcli stake show
Enter wallet name (default):
```

Enter your wallet name to display all of the hotkeys that have tao delegated to them.  This will include all active validators and miners.

# add

Adds stake to the desired hotkey

# remove

Remove stake from a hotkey
