---
title: 'CLI: Root'
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
The Root network is used by members of the root network to change subnet weights or to join & vote in the senate.

```
list                List the root network
weights             Set weights for root network.
get_weights         Get weights for root network.
boost               Boost weight for a specific subnet by increase amount.
slash               Slash weight for a specific subnet by decrease amount.
senate_vote         Vote on an active proposal by hash.
senate              View senate and it's members
register            Register a wallet to the root network.
proposals           View active triumvirate proposals and their status
delegate            Delegate Stake to an account.
undelegate          Undelegate Stake from an account.
my_delegates        Show all delegates where I am delegating a positive amount of stake
list_delegates      List all delegates on the network
nominate            Become a delegate on the network
```

# Set_default_take

Coming to the root subnet commands in May 2024.  This is a u16 value with allowed values 0-11,796.  This allows validators to customize that amount of emissions passed on to their delegates. To determine the validator's take, divide the value presented by 65535 and multiply by 100:

> 📘 Take examples
> 
> Take 11796.   11796/65535\*100 = 17.99% ~18% take.  This is the default.
> 
> 6553:    6553/65535\*100 = 9.999 ~10% take