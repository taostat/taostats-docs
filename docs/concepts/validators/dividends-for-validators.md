---
title: How are emissions calculated for Validators?
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

> 📘 **How we got here**
>
> [Subnet Emission: tao and alpha](/docs/subnet-emissions)
>
> [Alpha Distribution Mechanisms](/docs/subnet-mechanisms)

## VTrust

1. Validators test miners and create a weighted list of scores. These are submitted to Yuma Consensus.
2. These scores are compared to the other validators — each validator is judged to be *in consensus* with the rest of the validators.

If a validator is judged to be out of consensus, their VTrust (validator trust) decreases. VTrust is a value between 0 and 1, where 0 is terrible and 1 is perfect.

## [Stake Weight](/docs/stake-weight)

The other input to validator emissions is stake weight. Validators with higher stake weight receive higher emissions.

* **root_stake**: TAO staked to a validator on root.
* **tao_weight**: defined on chain as 0.18.
* **alpha_stake**: alpha staked to a validator on the subnet.
* **total_stake**: the value used to determine emissions.

<Image border={false} alt="formula" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/math/994be5fc7666f898.png" />

## Dividends

Dividends are the percentage of total validator emissions awarded to each validator. They are calculated from VTrust and `total_stake`. High stake and high VTrust lead to high dividends, and high dividends yield high emissions.

* The sum of all dividends on a subnet is 1.
* The dividend score is calculated once per tempo (360 blocks for most subnets).

# Calculating Validator Emission

<Image border={false} alt="Diagram splitting emission by percentage among subnet owner, validators, and miners, with the validator share routed through child/parent hotkey allocations" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/d287817a1c5644e6.png" />

* Validators receive 41% of the `alpha_out` subnet emission.
* The validator's dividend score gives the fraction of the validator alpha that is awarded.

> 📘 **Emission math example**
>
> A subnet receives 1 `alpha_out` per block.
>
> In 1 epoch: 1 × 360 = 360 alpha.
>
> Validators receive 41% of the subnet's emissions: 360 × 0.41 = 147.6 alpha.
>
> Validator X has dividends of 0.006: 147.6 × 0.006 = 0.8856 alpha per epoch.
>
> If this validator has parent hotkeys, this is divided amongst the validators based on stake (see [Emission for Parent/Child Hotkeys](/docs/emission-parent-hotkeys)).
>
> It is then divided into root emission (converted to TAO) and alpha emission — see [Emissions: Root vs. Alpha Stake](/docs/stakeholder-emissions-root-vs-alpha).

## Validator rewards

The validator's subnet emission is further split by several factors:

* Parent hotkeys receive their percentage of the stake.
  * The validator may take a `child_take` from this emission.
* Each subnet has a root:alpha proportion that divides the emissions.
* Both alpha and root proportions may have a validator take.
  * **This is the reward for the validator.**
* The remaining root and alpha reward is divided amongst stake nominators.

## Next Steps

* [Emission for Parent/Child Hotkeys](/docs/emission-parent-hotkeys) — dividing dividends to parent/child hotkeys.
* [Emissions: Root vs. Alpha Stake](/docs/stakeholder-emissions-root-vs-alpha) — dividing between root & alpha proportions.
* [Stakeholder Emissions: Root](/docs/stakeholder-emissions-root) & [Stakeholder Emissions: Alpha](/docs/stakeholder-emissions-alpha) — distribution of emissions to stakeholders.
