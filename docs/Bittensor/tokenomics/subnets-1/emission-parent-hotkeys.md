---
title: Emission for Parent/Child Hotkeys
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
Parent hotkeys are validators that do not run infrastructure in a subnet.  They use their stake as a parent hotkey to a validator running infrastructure (the child hotkey).

Parent hotkeys have all of the same abilities as child hotkeys. 

- Delegators may stake alpha on a parent hotkey inside a subnet.
- Delegators staked on root receive root stake from parent hotkeys.

> 📘 How we got here:
> 
> [Subnet Emission tao and alpha](doc:subnet-emissions)
> 
> [Distribution of alpha_out to participants](doc:distribution-of-alpha-in-a-subnet)
> 
> [Emissions for Validators](doc:incentive-for-validators)

# Calculating emissions for Parent/Child hotkeys

> 📘 Example
> 
> Taostats is the validator
> 
> ![](https://files.readme.io/28ef58edc6d3e9d11713064a6aa00fe832605a2ef45a821926666e265f14be72-image.png)
> 
> There are two parent hotkeys:
> 
> ![](https://files.readme.io/b3f944b6273ea499e4aa8295ba96d6ad3ca511cd73e3d9c09a63b11d93933a38-image.png)

<br />

The validator running the child hotkey (running the validation infrastructure) can impose a `child hotkey take` on any validator running a parent hotkey.  In the screenshot above the child hotkey take is set at 4.5%.

### Step 1: Find the tao and alpha staked to the hotkey

First, we determine the amount of tao and alpha each validator has on this hotkey:

- Taostats has 8/9 of its stake 
- parent_1 has 50% of its stake on this child hotkey
- parent_2 has 100% of its stake on the child hotkey.

<br />

![](https://files.readme.io/30058203a8c6ae4f811775c0042c6085c05c6b97f210680303d5fb84344df754-image.png)

### Step 2:  Determine the total stake of each validator

`tao_weight = 0.18`

![](https://files.readme.io/03743dc3602dea3bda31750015f68730d94e7325cb4e7bfe44cfbcf60b6b3843-image.png)

![](https://files.readme.io/b426947735e69ecd7596e379b758a4bc0ac818267731b003f472befebdebeeae-image.png)

### Step 3: Find the Percentage of total stake, and apply it to the dividends.

The 0..15 dividends are split based on the % of total stake for each validator

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c1b3ad216dad0f26b5434bfa3b42904a22ae8da4a37ff7391efa4401a815bf14-image.png",
        null,
        ""
      ],
      "align": "center"
    }
  ]
}
[/block]


<br />

### Step 4: Apply child hotkey take to parents

Taostats has a 4.5% child hotkey take.  Remove 4.5% of the dividends from each parent, and apply the proceeds to taostats.

![](https://files.readme.io/eed58b0aa184894c92a762ff8cf89cd24af8c844a0b0682dbe408e24edec680a-image.png)

0.000102 and 0.003372 are taken from parent_1 and parent_2, and added to taostats' final dividends.

### Step 5: Repeat this math for all child hotkeys.

Taostats has 1/9 of its stake on another validator.

Parent_1 has 50% of its stake on other validators.

Sum these dividends for all hotkeys in a subnet to get the final dividends for a validator on a subnet.

> 📘 Child Hotkey Take
> 
> Note that the child hotkey take collected by the child hotkey is added to the dividends of the validator.
> 
> This means that most of the child hotkey take is distributed to the stakeholders of the validator, and it is not directly deposited to the vlidator's wallet.

## Next Steps:

The remaining dividends are then divided amongst stakeholders.  

- [Emissions: Root vs. Alpha Stake](doc:stakeholder-emissions-root-vs-alpha)
- [Stakeholder Emissions: Root](doc:stakeholder-emissions-root)
- [Stakeholder Emissions: Alpha](doc:stakeholder-emissions-alpha)