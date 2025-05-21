---
title: Wallet balances
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
To get balances from any wallet:

# coldkey balance

```python
import bittensor as bt
sub = bt.subtensor( network = 'finney' )
ck='<coldkey>'
balance = sub.get_balance(address = ck)
```

<br>

# hotkey balances

You can get the balance for all the hotkeys associated with a cold key. This will print an array of all hotkeys and their current balance.

```
import bittensor as bt
sub = bt.subtensor( network = 'finney' )
ck='<coldkey>'
delegated = sub.get_stake_info_for_coldkey(ck)
print( delegated)
```

The following code will return the sum of all the hotkey stake:

```python
import bittensor as bt
sub = bt.subtensor( network = 'finney' )
ck='<coldkey>'

#this gets all hotkeys - both validators&miners as well as delegated/staked
total_st = sub.get_total_stake_for_coldkey(ck)
```

<br>