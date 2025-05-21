---
title: Parent Hotkey Validation
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
In September 2024, the Bittensor chain launched parent hotkeys - a way for validators to earn tao from stake, without actually running a validator on the chain.

## Parent hotkeys

A parent hotkey allows a validator to add their stake to an existing validator.  This increases the total stake for that validator on the subnet.\
For example, at the time of this screenshot, taostats has a total stake of 889k tao on Subnet 6, from taostats and 2 parent validators:

![](https://files.readme.io/40ae680af91c2dcb5e8ea48c52f621f5d86deaece2be9b88f89272d04af40ac3-image.png)

<br />

For the benefit of being a parent hotkey, taostats charges a child take of 4.5% - so the returns of PRValidator and Love are reduced by 4.5%,  and the 4.5% is distributed to taostats and their stakeholders.

## Why Parent hotkey?

* A parent hotkey does not need to run a neuron.
* Can begin building a validator while validating (many subnets have minimum stake requirements.)

<br />

## Can parent hotkeys “beat” existing validator returns?

Based on our research, if the parent hotkey chooses child validators with high Vtrust, the parent hotkey can have competitive returns, but they will never have higher returns than the validator they are parenting on.

### Math

For each child validator we use the taostats API to obtain:\
nom/1ktao/BTDay - describing the emissions of the validator\
child hotkey take on each subnet - describing the take 

As the child hotkey take varies across all subnets, we need to create a weighted child hotkey take (WCHT)

![](https://files.readme.io/4e04c8f06d1b51207e69eef596e3f9df6699dbde47317ed1a4f9df02c186f5bb-image.png)

<br />

We use the Subnet API endpoint to get the emissions for every subnet.  This acts as a weight - subnets with higher emission should have the child take weighted higher.than low emission subnets.

The emissions earned by a parent hotkey on this validator will be:

![](https://files.readme.io/48e1e1e604fe71995d3abb5335530dbe65d6adb9eeeb680c4744d711d11a80cb-image.png)

<br />

Doing this maths across top validators:\
          ~~'Axis': 0.48198,\
          'Ary van der Touw': 0.45515,\
    	'Owl Ventures': 0.43533~~\
    	'Taostats & Corcel': 0.41319,\
    	~~'Datura': 0.41136,~~\
    	'TAO-Validator.com': 0.4068,\
    	'RoundTable21': 0.40259,\
    	'Bittensor Guru': 0.40259,\
    	'Rizzo': 0.40198,\
    	'FirstTensor.com': 0.40137,

Weight copiers are listed with strikethrough.  Parent hotkeys who use only weight copiers will also be tagged as weight copiers on taostats.  There are 5 non-weight copying validators where a validator running parent hotkey can return a nom/1ktao/BTDay over 0.400 - which is competitive with many regular validators.
