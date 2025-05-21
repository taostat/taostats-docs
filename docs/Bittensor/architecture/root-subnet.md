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

The chart for subnet 0 resides on the [taostats.io](https://taostats.io) homepage.

[block:image]{"images":[{"image":["https://files.readme.io/7e940a7a68e59905d54c09677d29c7b385f75ed174cead5b960dcf7311eca5c7-Screenshot_2024-09-03_at_17.39.21.jpg",null,null],"align":"center"}]}[/block]

In this chart, to actual emission for each subnet is listed in the top row in orange.  The weights placed by each validator are listed below.

# Root Subnet Emissions

Validators on the Root subnet can allocate a percentage of emissions to the root subnet. 

Any emissions granted to the root subnet are recycled and not issued.  For example, if Subnet 0 has 12% emissions, 864 tao would be recycled a day, effectively reducing the daily tao emissions to  6,336 (7,200-864).  

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f21e9c8dd58487e6a2b39dfffcf0a68e8a23dee49bd62e840e8c6a93a0510e6c-Screenshot_2024-09-03_at_17.39.21.jpg",
        null,
        ""
      ],
      "align": "center",
      "sizing": "75% "
    }
  ]
}
[/block]


Recycling of emission is a safety mechanism in case emissions ever needed to be halted or reduced without needing to halt the  network itself.