---
title: Emissions for Validators
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
> 📘 How we got here
> 
> [Subnet Emission tao and alpha](doc:subnet-emissions)
> 
> [Distribution of alpha_out to participants](doc:distribution-of-alpha-in-a-subnet)

<br />

# How are emissions calculated for Validators?

# Terms to know

## VTrust

1. Validators test miners and create a weighted list of scores.  These are submitted to the Yuma consensus.
2. These scores are compared to the other validators - and each validator is judged to be _in consensus_ with the rest of the validators.

If a Validator is judged to be out of consensus, their VTrust (validator trust) will decrease. VTrust is a value between 0 and 1, where 0 is terrible, and 1 is perfect.

## Stake

The other value in the determination of validator emissions is the stake value.  Validators with higher stake will receive higher emissions.  

- **root_stake**: The amount of tao staked to a validator on root.
- **alpha_stake**: The amount of alpha staked to a validator on the subnet
- **total_stake**: The value used to determine emissions. tao_weight is defined on chain as 0.18.

  ![](https://files.readme.io/d585383ab0a61abd5f219a23d799f7eca283035c48b6c1109c3d8db4b207ad63-image.png)

<br />

## Dividends

Dividends are the percentage of the total validator emissions that will be given to each validator. It is calculated from Vtrust and total_stake. High stake & high VTrust lead to high dividends.  High dividends yield high emissions.

- The sum of all dividends on a subnet is 1.
- Dividend score is calculated once per tempo (360 blocks for most subnets).

# Calculating Validator Emission

![](https://files.readme.io/831e249de6a2f1ffbce72bc2043c9d5e1ebe2509483abf30b24411605a53cbb5-image.png)

<br />

- Validators receive 41% of the `alpha_out` subnet emission.
- The validator's dividend score gives the fraction of the Validator alpha that is awarded.

> 📘 Emission math example
> 
> A subnet receives 1 `alpha_out` per block.
> 
> In 1 epoch - 1\*360 =  360 alpha.
> 
> Validators receive 41% of the subnet' emissions. 360\*.41 = 147.6 alpha
> 
> Validator x has dividends of 0.006.  147.6\*0.006 = .8856 alpha per epoch.
> 
> \_Validator x has 0.8856 alpha emission. This will then be divided into root emission (and converted into tao) and alpha emission - awared to stakehodlers holding alpha.

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FBd4-eyGa1o0%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DBd4-eyGa1o0&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FBd4-eyGa1o0%2Fhqdefault.jpg&key=7788cb384c9f4d5dbbdbeffd9fe4b92f&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen; encrypted-media; picture-in-picture;\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=Bd4-eyGa1o0",
  "title": "Bittensor: What are validator Dividends and how are they calculated",
  "favicon": "https://www.youtube.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/Bd4-eyGa1o0/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=Bd4-eyGa1o0",
  "typeOfEmbed": "youtube"
}
[/block]


## Validator rewards

We have calculated the emission to the validator, but this is further split by several factors:

- Parent hotkeys receive their percentage of the stake.
  - The validator may take a `child_take` from this emission.
- Each Subnet has a root: alpha proportion that divides the emissions.
- Both alpha and root proportions may have a validator take.
  - **This is the reward for the validator.**
- The remaining root and alpha reward is divided amongst stake nominators.

## Next Steps

- [Emission for Parent/Child Hotkeys](doc:emission-parent-hotkeys): Dividing dividends to parent/child hotkeys.
- [Emissions: Root vs. Alpha Stake](doc:stakeholder-emissions-root-vs-alpha) Dividing between root & alpha proportions.
- [Stakeholder Emissions: Root](doc:stakeholder-emissions-root) & [Stakeholder Emissions: Alpha](doc:stakeholder-emissions-alpha): distribution of emissions to stakeholders.