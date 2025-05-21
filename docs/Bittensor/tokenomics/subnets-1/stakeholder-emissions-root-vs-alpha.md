---
title: 'Emissions: Root vs. Alpha Stake'
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
> 📘 How we got here:
> 
> [Subnet Emission tao and alpha](doc:subnet-emissions)
> 
> [Distribution of alpha_out to participants](doc:distribution-of-alpha-in-a-subnet)
> 
> [Emissions for Validators](doc:incentive-for-validators)
> 
> [Emission for Parent/Child Hotkeys](doc:emission-parent-hotkeys)

In the Bittensor ecosystem, holders of tao may stake to a validator in a subnet in two different ways:

- **Root stake **: Staking to a validator in subnet 0, the root subnet.
- **Alpha Stake**: Staking to a validator in a subnet, exchanging your tao for alpha token.

![](https://files.readme.io/2dbcfa4a1f65fa350e7699e6a30c5ec72ba9ed8f1e7bcafa24d511fee5301978-image.png)

<br />

The ratio of root: alpha staked is calculated using the `root_proportion`.

# Calculating root proportion

`root proportion` is calculated from 3 values:

- **tao on root**: The total amount of tao on root.
- **alpha issued**: The sum of `alpha_in` and `alpha_out` (all alpha emitted)
- **tao_weight**: a variable set by the chain.  The current `tao_weight` is 0.18.

![](https://files.readme.io/5fae38f32d8ae075ba7c970f88d69265de126147b67d21e03ccb5baff90381e5-image.png)

<br />

Root proportion will change every block, as the tao and alpha values will have increased (by 1 and 2 respectively).  The results can be charted over time:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9832735cab0abd57e776589bcaf69b38b0d312189b23dc91536d1b8c13014577-Screenshot_2025-02-03_at_22.27.36.jpg",
        null,
        "At day 0 there are 9M tao available."
      ],
      "align": "center",
      "caption": "On day 0 there is 6M tao available."
    }
  ]
}
[/block]


The chart will vary on the amount of tao available at the moment the subnet is created. The above chart shows day 0 = 6 million tao.  

On day 0 of the subnet, 100% of emission will go to root stakeholders.

50% root: 50% alpha is met at approximately day 70 (this is highly variable, and just an estimate).

<br />

In this second chart, the yellow/green subnet is created 100 days after the blue/red subnet (9,720,000 tao, and 0 alpha for the 2nd subnet):

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/59dbf6da25a6b277a17966e90f2e290c7006dc2464cd95653d3e291e4ef593cb-Screenshot_2025-02-03_at_22.28.59.jpg",
        null,
        ""
      ],
      "align": "center"
    }
  ]
}
[/block]


<br />

<br />

## Next steps

Now that the stake has been divided into root and subnet shares, we can divide these amongst the stakeholders.

[Stakeholder Emissions: Root](doc:stakeholder-emissions-root)

[Stakeholder Emissions: Alpha](doc:stakeholder-emissions-alpha)