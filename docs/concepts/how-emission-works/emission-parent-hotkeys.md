---
title: Calculating emissions for Parent/Child hotkeys
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

* Delegators may stake alpha on a parent hotkey inside a subnet.
* Delegators staked on root receive root stake from parent hotkeys.

> 📘 **Where we are — step 4 of the [emission flow](/docs/how-emission-works)**
>
> How we got here:
>
> 1. [TAO emission](/docs/tao-emission) — TAO split across subnets.
> 2. [Alpha emission](/docs/alpha-emission) — each subnet mints `alpha_in` + `alpha_out`.
> 3. [Split `alpha_out` among participants](/docs/split-alpha-out) — owner 18% / miners 41% / validators 41%.
>
> **This page (step 4):** aggregate each validator's dividends across its parent and child hotkeys.

> 📘 **Example**
>
> Taostats is the validator
>
> <Image border={false} alt="Spreadsheet row with columns for child, root stake, alpha stake, child hotkey take, amount parent staked, and dividends used in parent/child emission calc" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/659e50f203c0a9b8.png" />
>
> There are two parent hotkeys:
>
> <Image border={false} alt="Spreadsheet listing parent hotkeys with root stake, alpha stake, and stake-percentage columns as inputs to an emission calculation" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/897029852eda7c7f.png" />

The validator running the child hotkey (running the validation infrastructure) can impose a `child hotkey take` on any validator running a parent hotkey.  In the screenshot above the child hotkey take is set at 4.5%.

### Step 1: Find the tao and alpha staked to the hotkey

First, we determine the amount of tao and alpha each validator has on this hotkey:

* Taostats has 8/9 of its stake
* parent\_1 has 50% of its stake on this child hotkey
* parent\_2 has 100% of its stake on the child hotkey.

<Image border={false} alt="Spreadsheet mapping accounts (validator and two parents) to their tao and alpha stake columns for finding stake on a hotkey" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/6bf05da556ff86df.png" />

### Step 2:  Determine the total stake of each validator

`tao_weight = 0.18`

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/994be5fc7666f898.png" />

<Image border={false} alt="Spreadsheet with tao, alpha, and total-stake columns per validator, combining the two token stakes into one weighted total" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/3e89d967505bbd48.png" />

### Step 3: Find the Percentage of total stake, and apply it to the dividends.

The 0..15 dividends are split based on the % of total stake for each validator

<Image border={false} alt="Spreadsheet splitting a fixed dividend pool across validators proportionally by each one's percentage of total stake" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/b3095cad7eaea1cf.png" />

### Step 4: Apply child hotkey take to parents

Taostats has a 4.5% child hotkey take.  Remove 4.5% of the dividends from each parent, and apply the proceeds to taostats.

<Image border={false} alt="Spreadsheet applying a child hotkey take to each parent's dividends, showing dividends, take, and final dividends columns" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/89d789e5c478aa7f.png" />

0.000102 and 0.003372 are taken from parent\_1 and parent\_2, and added to taostats' final dividends.

### Step 5: Repeat this math for all child hotkeys.

Taostats has 1/9 of its stake on another validator.

Parent\_1 has 50% of its stake on other validators.

Sum these dividends for all hotkeys in a subnet to get the final dividends for a validator on a subnet.

> 📘 **Child Hotkey Take**
>
> Note that the child hotkey take collected by the child hotkey is added to the dividends of the validator.
>
> This means that most of the child hotkey take is distributed to the stakeholders of the validator, and it is not directly deposited to the validator's wallet.

## What's next

**Step 5 — [Root vs alpha split](/docs/stakeholder-emissions-root-vs-alpha):** the validator's remaining dividends are divided into a root proportion and an alpha proportion, then distributed to stakeholders ([root](/docs/stakeholder-emissions-root) / [alpha](/docs/stakeholder-emissions-alpha)).
