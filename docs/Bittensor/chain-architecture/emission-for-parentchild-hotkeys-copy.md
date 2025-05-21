---
title: Parent/Child Hotkeys
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
Child hotkeys add an additional layer of delegation possibilities.

A validator with stake now has three options:

1. Run a neuron on the subnet (as before).
2. No longer run a neuron, but act as a parent - supplying 100% of their stake to another validator (the child) on any subnet.
3. A mix.  Run a neuron with a percentage of stake, and act as a parent with your remaining stake to one or more validators running neurons.

# Parent vs. Child

## Parent Hotkey

A **parent hotkey** sets a proportion (from 1-100%) of their stake to another hotkey.  

## Child Hotkey

A **child hotkey** is a neuron running on the subnet. One or more parent hotkeys stake tao to the child hotkey.  The total stake of the child hotkey is the sum of the child's stake + the sum of the stakes provided by the parents.

# Identifying child hotkeys

On taostats, a child hotkey has a bright yellow stake.

In the screenshot below, the validator in position 1 has no parent stake, but the validator in position 2 *does* have parent hotkeys staking to it.

![](https://files.readme.io/bf3967ecb0f4a2e310f2ea03da72fe1fb21b1295e49dc575af74207d1ba910fd-image.png)

# Child hotkeys and emission

In the screenshot above, the validator in position 1 has emission of 1.93543.  100% of that emission goes to that validator, as there are no parent hotkeys.

But with child hotkeys, the emission is split between the child and the parents.  So the validator in position 2 share the 1.83997 emission with its parents.

Clicking the UID or the stake of the validator helps us better understand this division.

![](https://files.readme.io/f8f37fc7db7fcac1b370a2b1af0ecb95c04dbc39d84dc231dcea4144bc3ea1fc-image.png)

UID 2 is *Taostats and Corcel*.  It has 2 parent hotkeys: *PR Validator* and *Neural Internet*.  

## Calculating emission between parent and child hotkeys

[Emission for Parent/Child Hotkeys](doc:emission-parent-hotkeys)
