---
title: Staking in dTao
excerpt: Updated January 10, 2025
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
# TL;dr

Before dtao, you stake your tao on a validator.

In dtao, you stake your tao on a validator **ON A SUBNET**.  

# I have tao staked today. What happens when dTao starts?

![](https://files.readme.io/8b074c1b9ac46f8a5571ea669dacf2b340a57a428f6dac597c243d505235a129-image.png)

When dTao begins, Kieran's stake remains staked to Taostats.  But, since all tao must be staked to a validator on a subnet, his stake is moved to Taostats on subnet 0.

This is called **"staking to root."**

> 📘 All stake "pre-dTao" is converted to root stake.
> 
> Stakeholders do not have to do anything at dTao launch. Your tao remains staked to the same validator(s).

# Staking to root

Staking to root is _essentially_ the same as staking pre-dTao.  Select a validator present on the root subnet, and stake your tao on that validator.  You will begin to receive a proportion of the validator's earnings on each subnet where the validator is active.

## Is staking to root safe?

Staking is inherently safe your stake never leaves your wallet, so it cannot be accessed by the validator.

## Is staking to root risky?

Staking to root keeps your tao as tao, so there is no risk of slippage. When you unstake your tao, you will receive exactly the same amount you added. 

Note that the returns of staking on root will decrease over time - to roughly 20% of the returns possible pre-dTao. (see below for details)

# Staking to a subnet (not root)

> 📘 All subnet staking is in alpha token
> 
> Staking on a subnet is made using the token of the subnet.  The subnet tokens are given a letter from an alphabet (greek, hebrew, arabic, etc.) but are generically defined as 'alpha'.  (alpha is also the token of subnet 1, as it is the first letter in the greek alphabet)
> 
> Alpha tokens can only be purchased with tao.

In dtao, you stake to a validator **on a subnet**.  Assuming that the subnet is not root, you are completing a few transactions to stake.  You convert your tao to alpha, and the stake the alpha to a validator on the subnet.

## Is staking to a subnet safe?

Staking is inherently safe your stake never leaves your wallet, so it cannot be accessed by the validator.

## Is staking to a subnet risky?

**Staking to a subnet incurs more risk to tao loss.**  Converting tao to alpha incurs slippage.  If the alpha price should decrease, you will not receive the same amount of tao on an unstaking event.  It could be more - but it could also be less.

### Large staking events incur more slippage

See [Alpha Tokens](doc:alpha-tokens) for details on what slippage is, and how it is calculated.

<br />

<br />

# Ratio between root and alpha staking

For each subnet, there will be a ratio describing how the validation rewards are distributed. 

The ratio is determined by 3 values: 

- Amount of tao on root
- Amount of Alpha on subnet
- TAO Weight (set on chain at 10%)

<br />

When the subnet is created, 100% of staking emission will go to root as the root% = 100%. 

(Note that _subnet launch_ for existing subnets is the block where dtao launches)

![](https://files.readme.io/a1d8b7d200586cace4ec0bbfd7e27bfc973a6276fc331a4273df4a0f6cd59d9b-image.png)

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/824a92e85a4ce5dba612f58e3ea9ad05528ffb5b21beaa58320f122298c84096-Screenshot_2025-01-10_at_12.54.07.jpg",
        null,
        "Root/alpha emission for a Subnet starting with 9M tao in circulation at day 0. (This chart does account for the halvening at 10.5M blocks lowering tao and alpha emissions)"
      ],
      "align": "center",
      "caption": "Root/alpha emission for a Subnet starting with 9M tao in circulation at day 0. (This chart does account for the halvening at 10.5M blocks lowering tao and alpha emissions)"
    }
  ]
}
[/block]


> 📘 Note that this curve changes depending on how much tao is in circulation.
> 
> If a 2nd subnet registers 100 days after the first subnet, the curves are different
> 
> ![](https://files.readme.io/b6bdc96352007bef93af05bcc06eb350354939c97819783395fc6022eb297161-image.png)

### Here's the code

from pallets/src/run_coinbase.rs (line 27):

```rust
    pub fn get_root_divs_in_alpha(netuid: u16, alpha_out_emission: I96F32) -> I96F32 {
        // Get total TAO on root.
        let total_root_tao: I96F32 = I96F32::from_num(SubnetTAO::<T>::get(0));
        // Get total ALPHA on subnet.
        let total_alpha_issuance: I96F32 = I96F32::from_num(Self::get_alpha_issuance(netuid));
        // Get tao_weight
        let tao_weight: I96F32 = total_root_tao.saturating_mul(Self::get_tao_weight());
        // Get root proportional dividends.
        let root_proportion: I96F32 = tao_weight
            .checked_div(tao_weight.saturating_add(total_alpha_issuance))
            .unwrap_or(I96F32::from_num(0.0));
        // Get root proportion of alpha_out dividends.
        let root_divs_in_alpha: I96F32 = root_proportion
            .saturating_mul(alpha_out_emission)
            .saturating_mul(I96F32::from_num(0.41));
        // Return
        root_divs_in_alpha
    }
```