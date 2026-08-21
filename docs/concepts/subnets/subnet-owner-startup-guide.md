---
title: Designing a subnet
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

You've got a subnet idea, or you've just registered one. This guide takes you from initial design through launch.

The page is split into two halves:

- **Designing a subnet** — frameworks, incentive mechanism resources, prior-art talks. Useful pre-registration.
- **Launching your subnet** — identity, validator, starting emission, immunity, UID pruning. Useful post-registration.

For the broader concept of what a subnet owner _is_, see [Subnet Owner](/docs/subnet-owner).

## Incentive mechanism resources

Talk on validator setup and incentive design:

<Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=wZhgzMKc05I" href="https://www.youtube.com/watch?v=wZhgzMKc05I" providerUrl="https://www.youtube.com/" providerName="YouTube" />

* namoray spoke on the Bittensor Guru podcast about his vision of subnets in [Episode 20](https://bittensor.guru/episode-20-subnet-19-vision-w-namoray) — a good introduction to subnet creation.
* Rhef (Subnet 12) has published a [subnet guide](https://docs.google.com/document/d/10wRkMVv5rfjHtJwDYMZkMl4v6_MHtJEABK3X5aIXhdg/edit#heading=h.4y6sli8eoiyn) covering practical lessons from running a live subnet.

# Launching your subnet

## Subnet identity

Identity can be set at registration time, or changed later with `btcli s set-identity`. This is how Taostats shows your name, logo, and links.

Check the current identity with `btcli s get_identity`:

```
                      Current Subnet 1 Identity                       
                                                                      
           Item ┃ Value                                               
━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
         Netuid │ 1                                                   
    subnet_name │ Apex                                                
    github_repo │ https://github.com/macrocosm-os/apex                
 subnet_contact │ support@macrocosmos.ai                              
     subnet_url │ https://apex.macrocosmos.ai                         
        discord │ macrocrux                                           
    description │ Building the world's fastest deep researchers       
       logo_url │ https://www.macrocosmos.ai/images/mc_logo_black.png 
     additional │ ~                                                   
────────────────┼─────────────────────────────────────────────────────
                │                                                     

```

> 📘 **Tips for setting identity**
>
> The biggest pitfall is the logo URL.
>
> The `logo_url` **must** be the URL of the raw image — not the URL of a page hosting the image.
>
> For example:
>
> ❌ `https://github.com/taostat/.github/blob/main/profile/taostats.png`
>
> This is a page hosting the image. Right-click the image and open it in a new tab to find the raw URL.
>
> ✅ `https://raw.githubusercontent.com/taostat/.github/refs/heads/main/profile/taostats.png`
>
> This is the link to the image served directly by GitHub. Use this form.

## Immune owner neurons

Owners can set how many immune neurons they have via the `ImmuneOwnerUidsLimit` parameter. The default is 1; the max is 10.

## Running a validator

All subnet owners have at least one neuron that cannot be deregistered. This is intended to be run as a validator:

* Validators provide access to the subnet's commodity. With a validator, you have access to your own commodity.
* Mining emission to this hotkey is burned (see [Subnet Owner Neuron](/docs/#subnet-owner-neuron) for details). The owner cannot run a miner on this hotkey to receive alpha.

### Setting up a validator

* Make sure your validator is setting weights.
* Work with other validators to ensure they are running the subnet code and that your validator is in consensus.

## Starting emission

Subnets on registration are not active. Run `btcli subnet start` to start emission on your subnet.

## Subnet immunity

You have 4 months of immunity from registration to build up your subnet. After 4 months, if your subnet has the lowest moving price, it may be deregistered.

## UID pruning

At launch your subnet has 256 UIDs. This can be reduced to a lower number.

## Subnet mechanisms

Subnet mechanisms are a way to run different tasks on a single subnet. See [Subnet Architecture — Subnet Mechanisms](/docs/#subnet-mechanisms-formerly-subsubnets) for the current implementation.

## What's next

* Once your subnet is live, your emission share is governed by the demand formula (price EMA with miner-burn scaling) feeding the spec 440 emission gate. See [Subnet Emissions](/docs/subnet-emissions) for how emission is computed and its implications for owner self-emission.
* See [Subnet Owner](/docs/subnet-owner) for the broader role and responsibilities of a subnet owner.
