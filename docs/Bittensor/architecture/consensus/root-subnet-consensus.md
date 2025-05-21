---
title: Subnet Emission Consensus
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
# Current State

Subnet emission is determined on the root subnet by validators placing weights.

> 📘 Learn more about the mechanisms behind root emissions:
> 
> - [Subnet Emissions](doc:subnet-emissions)
> - [Root Subnet](doc:root-subnet)

To review the weights placed by validators on each subnet, the taostats homepage displays the **Root Metagraph**.  

- The header row shows the emission % for each subnet.
- Each row displays a validator, and the weights placed by that validator on each subnet.

![](https://files.readme.io/838eee2a64874cf861f7fad3dca3dff2088c2393426566f1eebc5ff25cb8492f-image.png)

# Consensus amongst the Validators

There is a wide variety of weights being placed by validators.  Many validators are close to Yuma Consensus in each subnet. Some validators have large variation from consensus. 

In order to better illustrate the differences in weights from Yuma Consensus, we have added colors to the chart to help distinguish weights that are outliers.

## Explaining the colors:

- **White**: within ONE standard deviation of Yuma Consensus.
- **Yellow** Between ONE and TWO standard deviations of Yuma Consensus.
- **Orange** Over TWO standard deviations from Yuma Consensus.

## More details:

In the analytics section of Taostats, we have an even more verbose version of the Root Metagraph chart: [Validator Weights Deviation](https://taostats.io/deviation) 

This chart also displays in parentheses the number of standard deviations from Yuma for each weight. (see Math below for calculation details).

![](https://files.readme.io/c07fe9416196785ac872e388a352918e0ed66d6223775a7aed505f0cc5d69abd-image.png)

In the screenshot above there are three scores that are over 1 standard deviation from Consensus:

- **Taostats SN 4**: is 1.2 standard deviations below Yuma.
- **OTF SN0**:  1.1 standard deviations above Yuma
- **OTF  SN1: **-1.0 standard deviations below Yuma.

The **Deviation** column is the average of the deviations from Yuma across all Subnets for a validator. (We take the absolute values of the Standard Deviation, as it is the overall magnitude of the deviation - not the _direction_ of the deviation that we are concerned about.)

<br />

# Math

Subnet weights are **not** normal distributions, but we will use means and standard deviations to determine deltas from Yuma.  

- **Mean**: We use Yuma Consensus emission as the mean (it is a weighted mean to a degree)
- ** Standard Deviation**: There are a few caveats to how we have calculated Standard Deviation:

  - We ignore all weights of 0 when finding the standard deviation.
  - Subnets with very low emission end up with very weird standard deviations. so the smallest standard deviation is 1%. (If a subnet has emission of 0.65%, 1.65% is one standard deviation away, 2.65 is two standard deviations away.)

  ![](https://files.readme.io/1fa86dc9e74ba5dc2e9f731f672819278ff94934cddaa3a11eb6357141e8964b-image.png)

  > 📘 What is standard deviation?
  > 
  > In a normal distribution:
  > 
  > - 68% of entries are within 1 standard deviation (zindex between -1 and 1)
  > - 95%
- **Validator Deviation**: This can also be called the Z-Index.  If it is >1 or \<-1, it is more than one standard deviation from the mean. (if >2 or \<-2 it is more than two standard deviations form the mean)

![](https://files.readme.io/05145bfc885a43f5f6175e6526f80fe12890154b3825bd76e6a87406cf559a79-image.png)

<br />

- **Deviation**:  This is the average of the absolute values of Validator Deviation. We used the absolute value of the deviation so that positive and negative deviations do not cancel each other out.  This tells us the overall magnitude of all the differences - and then we can calculate the average.