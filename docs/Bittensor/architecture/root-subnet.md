---
title: Root Subnet
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
The root subnet has the netuid of 0.  Its current role is to define how emissions are distributed across the other Bittensor subnets. It is limited to 64 neurons and each neuron must be a validator.

Validators set weights for each of the subnets, assigning a score to each subnet based the value proposition they contribute to the network.  These weights are fed into Yuma Consensus to create network subnet emissions and control the distribution ratio of tao to the subnets.  The overall distribution percentages are listed in the top row of the chart.

If emissions are assigned to netuid 0 by any or all validators, then that tao would be recycled back into unissued tokens. this is a safety mechanism in case emissions ever needed to be halted or reduced without needing to halt the  network itself.

The chart for subnet 0 resides on the [taostats.io](https://taostats.io) homepage.

![](https://files.readme.io/e2e24a6-image.png)

# Root Subnet Emissions

Validators on the Root subnet can allocate a percentage of emissions to the root subnet. 

Any emissions granted to the root subnet are recycled and not issued.  For example, if Subnet 0 has 1% emissions, 72 tao would be recycled a day, effectively reducing the daily tao emissions to  7,198 (7,200-72).  

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8882112-image.png",
        null,
        ""
      ],
      "align": "center",
      "sizing": "50% "
    }
  ]
}
[/block]