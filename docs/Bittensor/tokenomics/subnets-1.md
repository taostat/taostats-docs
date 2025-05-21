---
title: Subnet Emission
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
In this series of pages, we'll walk through the process of how tao and alpha are distributed to participants of a subnet.

![](https://files.readme.io/2c1db4fcec6e6e3dfae53813ea1a06842bb6ca7836973c4d859e172e88fc835b-image.png)

<br />

Step 1: [Subnet Emission Distribution](doc:subnet-emissions): How emitted tao is split amongst the subnets.

Step 2: [Alpha Emission](doc:alpha-emission): Up to 2 alpha is emitted per subnet per block.  This page describes the split between the Subnet Pool (alpha_in) and subnet participants (alpha_out).

Step 3: Split `alpha_out` to SN owner/miners/validators.

- Subnet owners receive 18% of subnet emission
- [Emission for Miners](doc:consensus-for-miners): Miners receive 41% of emissions. 
- [Emissions for Validators](doc:incentive-for-validators): Validators receive 41% of emissions, but this is also divided amongst stakeholders.

Step 4: [Emission for Parent/Child Hotkeys](doc:emission-parent-hotkeys):  Sum the rewards across all parent and child hotkeys for each validator.

Step 5: [Emissions: Root vs. Alpha Stake](doc:stakeholder-emissions-root-vs-alpha): Divide the validator's dividends into root and alpha proportions.

Step 6: Award stakeholder rewards to root & alpha stakeholders:

- [Stakeholder Emissions: Root](doc:stakeholder-emissions-root)
- [Stakeholder Emissions: Alpha](doc:stakeholder-emissions-alpha)