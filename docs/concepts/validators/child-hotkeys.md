---
title: Child & Parent Hotkeys
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

A **child hotkey** lets a validator delegate a portion of its stake weight to another hotkey, which validates on its behalf. The parent retains ownership of the stake; the child earns a configurable **childkey take** on the emissions it produces.

Parent hotkeys launched on the Bittensor chain in September 2024 — a way for a stakeholder to earn TAO from stake without running a validator themselves.

> 📘 For how child hotkeys affect validator returns and emissions, see [Validation](/docs/validation) and [Emission and parent hotkeys](/docs/emission-parent-hotkeys).

## Key points

* **Parent hotkey:** owns the stake and assigns weight to one or more child hotkeys. It adds its stake to an existing validator, increasing that validator's total stake on the subnet.
* **Child hotkey:** validates using delegated weight and takes a childkey cut of the resulting emission.
* Child/parent relationships are factored into every per-subnet validator return calculation.

## Why use a parent hotkey?

* A parent hotkey does not need to run a neuron.
* You can begin building a validator while already validating — many subnets have minimum stake requirements, and parenting lets you participate below your own competitive floor.

## Parent hotkeys on Taostats

In the subnet metagraph, a yellow stake value indicates parent hotkeys. Clicking the caret opens a view showing all of the parents (and the percentage of their stake) added to the child hotkey.

<Image border={false} alt="Subnet metagraph table row whose yellow stake weight expands into a nested Child/Parent panel listing hotkeys with stake, root stake, and alpha weight" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/00bfddcc6ca59a7d.png" />

For the benefit of being a parent hotkey, Taostats charges a child take of 4.5% — the parent's returns are reduced by 4.5%, which is distributed to Taostats and its stakeholders.

## Can parent hotkeys "beat" existing validator returns?

If the parent hotkey chooses child validators with high VTrust, it can achieve competitive returns — but it will never earn higher returns than the validator it is parenting on.

## Related

* [Validation](/docs/validation)
* [Emission and parent hotkeys](/docs/emission-parent-hotkeys)
* [Dividends for Validators](/docs/dividends-for-validators)
