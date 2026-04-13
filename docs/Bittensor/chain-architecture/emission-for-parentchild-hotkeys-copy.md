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

![](https://files.readme.io/cff853c815003080a78d3ab09ab2e00d059c1342b9a1b89b47e4cae65c0c1b1f-image.png)

# Child hotkeys and emission

In the screenshot above, the validatorOwner64 in position 5 has 40,265 alpha staked, and 100% of that emission goes it it's stakeholders, there are no child hotkeys.

MUV in position 4 has 66,290 alpha staked, but some comes from child hotkeys.

But with child hotkeys, the emission is split between the child and the parents.  Clicking the carat shows the stake breakdown:

![](https://files.readme.io/0b84d42d9c45455f6c947d3d2893db84f10a4a67f57be2e7145212e6294c216e-image.png)

# Child Hotkey Take

Child hotkeys - those running infrastructure - can impose a child hotkey take - a percentage of the earnings for each parent hotkey. This can range from 0-18%.

## Calculating emission between parent and child hotkeys

[Emission for Parent/Child Hotkeys](doc:emission-parent-hotkeys)