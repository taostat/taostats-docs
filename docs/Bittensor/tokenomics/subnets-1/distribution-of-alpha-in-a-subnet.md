---
title: Distribution of alpha_out to participants
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
Every block distributes tao and alpha into every subnet.

See [Subnet Emission tao and alpha](doc:subnet-emissions) for details.

# `alpha_out` distribution

<br />

Each subnet's incentive mechanism breaks down the distribution of the Subnet's `alpha_out` to the active participants of the subnet.  There is 1 `alpha_out` every block. (until alpha reaches it's [Halving](doc:halving).)

<br />

## Subnet mechanisms

Each subnet can have multiple mechanisms (they were formerly called sub subnets.). This means that each subnet can work to solve multiple challenges.  In V1 of subnet mechanisms, all miners and validators can compete in all mechanisms.

The subnet owner can divide the `alpha_out` distribution to the subnet mechanisms as a mechanism percentage:

```
   pub fn sudo_set_mechanism_emission_split(
            origin: OriginFor<T>,
            netuid: NetUid,
            maybe_split: Option<Vec<u16>>,
```

The `maybe_split` vector is used to divide the subnet's emission amongst subnet mechanisms.

<Callout icon="📘" theme="info">
  Examples

  If there are 2 mechanisms, they might be split evently 50:50.  Or a subnet with new subnet mechanism might want to start that new mechanism at a lower value (90:10).
</Callout>

Eventually, there will be a maximum of 8 subnet mechanisms allowed per subnet.

## In each mechanism

* **Subnet Owner**: The subnet owner receives 18% of the emissions. (0.18 alpha)
* **Miners** Miners split 41% of emissions. (0.41 alpha)
* **Validator** Validators (and their stakeholders) split 41% of emissions. (0.41 alpha)

<Image align="center" alt="Emission breakdown of Subnet 19: 18% to owner, 41% to Miners & Validators." border={false} caption="Emission breakdown of Subnet 19: 18% to owner, 41% to Miners & Validators." src="https://files.readme.io/14578d321b33b4d9a6d1de35af5acb919f4baee021c16faad77d059f0f351817-image.png" />

## **Individual Miner** rewards

* Miners are awarded emissions based on their incentive score.
* The sum of `incentive` across all of the validators in a subnet is equal to 1.
* `incentive` is updated every tempo (generally 360 blocks).
* Miners receive `alpha_out` * .0.41 * `incentive` *360 every tempo for each subnet mechanism.
* The incentive received in each mechanism is weighted by the mechanism split, and the sum is awarded to the miner.

See [Emission for Miners](doc:consensus-for-miners)for more details on how incentive is awarded to miners.

## **Individual Validator** rewards

* Validator rewards are calculated on each submechanism, and aggregated to the subnet through the mechanism split weighting.
* Subnet validator rewards are split between the validator and their stakeholders.
* Validators with higher VTrust and higher stake (both root and alpha) will receive higher rewards.
* [Parent/Child Hotkeys](doc:emission-parent-hotkeys) play a role in how how validator rewards are returned.
* Validator rewards are returned in tao and alpha, as stakeholders can hold [Root and Alpha stake](doc:stakeholder-emissions-root-vs-alpha).

See [Emissions for Validators](doc:incentive-for-validators) for detail on how incentive is awarded to validators.
