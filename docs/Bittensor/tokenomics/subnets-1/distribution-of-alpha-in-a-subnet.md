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

Each subnet's incentive mechanism breaks down the distribution of the Subnet's `alpha_out` to the active participants of the subnet.  There is 1 `alpha_out` every block.

* **Subnet Owner**: The subnet owner receives 18% of the emissions. (0.18 alpha)
* **Miners** Miners split 41% of emissions. (0.41 alpha)
* **Validator** Validators (and their stakeholders) split 41% of emissions. (0.41 alpha)

<Image alt="Emission breakdown of Subnet 19: 18% to owner, 41% to Miners & Validators." align="center" src="https://files.readme.io/14578d321b33b4d9a6d1de35af5acb919f4baee021c16faad77d059f0f351817-image.png">
  Emission breakdown of Subnet 19: 18% to owner, 41% to Miners & Validators.
</Image>

## **Individual Miner** rewards

* Miners are awarded emissions based on their incentive score. 
* The sum of `incentive` across all of the validators in a subnet is equal to 1.
* `incentive` is updated every tempo (generally 360 blocks).
* Miners receive `alpha_out` \* .0.41 \* `incentive` \*360 every tempo.

See [Emission for Miners](doc:consensus-for-miners)for more details on how incentive is awarded to miners.

## **Individual Validator** rewards

* Validator rewards are split between the validator and their stakeholders.
* Validators with higher VTrust and higher stake (both root and alpha) will receive higher rewards.
* [Parent/Child Hotkeys](doc:emission-parent-hotkeys) play a role in how how validator rewards are returned.
* Validator rewards are returned in tao and alpha, as stakeholders can hold [Root and Alpha stake](doc:stakeholder-emissions-root-vs-alpha).

See [Emissions for Validators](doc:incentive-for-validators) for detail on how incentive is awarded to validators.
