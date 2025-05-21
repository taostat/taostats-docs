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

In the screenshot below, the validator in position 1 has no parent stake, but the validator in position 2 _does_ have parent hotkeys staking to it.

![](https://files.readme.io/bf3967ecb0f4a2e310f2ea03da72fe1fb21b1295e49dc575af74207d1ba910fd-image.png)

# Child hotkeys and emission

In the screenshot above, the validator in position 1 has emission of 1.93543.  100% of that emission goes to that validator, as there are no parent hotkeys.

But with child hotkeys, the emission is split between the child and the parents.  So the validator in position 2 share the 1.83997 emission with its parents.

Clicking the UID or the stake of the validator helps us better understand this division.

![](https://files.readme.io/f8f37fc7db7fcac1b370a2b1af0ecb95c04dbc39d84dc231dcea4144bc3ea1fc-image.png)

UID 2 is _Taostats and Corcel_.  It has 2 parent hotkeys: _PR Validator_ and _Neural Internet_.  

## Calculating emission between parent and child hotkeys

PR Validator and Neural Internet have contributed  100% of their tao to the taostats validator. Emission between the three hotkeys is divided based on the percentage of stake (taostats 92.3%,  PR Validator 4.8% and Neural Internet 2.8%).

However, Taostats is running the infrastructure for this validator, and as the child hotkey can add a **Child Take**: a percentage of the emission from the parent hotkeys (in the screenshot above, we can see this is 4.5%).  That 4.5% is taken from PR Validator and Neural Internet to the taostats validator (and its delegates).

![](https://files.readme.io/bee7bd35932af0de81248500fbfd29f813232a06ae9005d1151e792e218b7b38-image.png)

# Why use Child Hotkeys

**Parent Hotkey:** PR Validator and Neural Internet have significant stake.  By setting their hotkeys as parents, they no longer have to run infrastructure to earn emissions (the childkey take is likely less than the cost of the infrastructure that was being maintained.). Parents can have different children on every subnet.

For the **child hotkey**, emissions are increased by adding the child take.  This increases the return to those that stake with the child hotkey. The child hotkey also has a higher percentage of the stake in the subnet, allowing for greater access to the knowledge created by the miners.

# Who Benefits from Child hotkeys?

There are 4 parties involved with child hotkeys:

- Child Validator
- Child Validator stakeholders
- Parent Validator
- Parent Validator stakeholders

For this analysis, let's assume the parent could run a validator on the subnet with exactly the same quality (VTrust) as the child.

> 📘 We expect that most childkey takes will be set between 0-9%, as this range provides the most benefit for all participants.

## Child take = 0%

- <span style="color:red">Child Validator: No benefit. Increased traffic on infrastructure.</span>
- Child Validator stakeholders: No benefit
- <span style="color:green">Parent Validator: Same returns as child validator</span>
- <span style="color:green">Parent Validator stakeholders: Same returns as child validator</span>

## Child take = (0-19)%

- <span style="color:green">Child Validator: Increase of returns.</span>
- <span style="color:green">Child Validator stakeholders: Increase of returns</span>
- <span style="color:yellow">Parent Validator</span>
- <span style="color:yellow">Parent Validator stakeholders</span>

> 📘 As a parent validator: compare the costs of running a validator, and if you are able to match the returns of the child validator.
> 
> Choosing a child with a very high nom/1k/day ensures that despite a childkey take, you are maximizing your returns.

> 📘 As a child validator balance increased returns with other childkey takes.  If you cannot promise as high a return as other validators, the parent hotkeys will move.

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FH3QZRl8RyK0%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DH3QZRl8RyK0&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FH3QZRl8RyK0%2Fhqdefault.jpg&key=02466f963b9b4bb8845a05b53d3235d7&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen; encrypted-media; picture-in-picture;\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=H3QZRl8RyK0",
  "title": "Bittensor: Validator emission October 2024",
  "favicon": "https://www.google.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/H3QZRl8RyK0/hqdefault.jpg",
  "provider": "https://www.youtube.com/",
  "href": "https://www.youtube.com/watch?v=H3QZRl8RyK0",
  "typeOfEmbed": "youtube"
}
[/block]