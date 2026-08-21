---
title: Miner Incentive Distribution
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

There are three miner distribution charts

This chart shows the incentive values for all miners on the subnet.  The lowest active key shows where the cutoff is for active miners, and the next UID to be expelled on new registration.   The shape of the chart is an indication of how competitive a subnet is (a narrow distribution indicates a competitive subnet where all miners are at risk of re-registration(.

<Image border={false} alt="Taostats miner incentive distribution scatter plot of incentive against sorted miner UIDs with a lowest-active-key cutoff line and active/immune coloring" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/3984b3d00601a299.png" />

Also note that this table can be animated to see how the distribution changes over time.

# Miner Coldkey Distribution

Each miner has a unique hotkey, but the hotkeys can be controlled by a single coldkey.  This chart displays how many organizations are running multiple miners in the subnet.

<Image border={false} alt="Taostats miner coldkey distribution as a segmented proportional bar where each slice sizes a coldkey's share of miner hotkeys, with squares/linear view toggle" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/9c76761af8ce5aa1.png" />

# Miner IP Distribution

Breakdown of Miners by IP addresses.

<Image border={false} alt="Taostats miner IP distribution as a segmented proportional bar sized by miners per IP address, with squares/linear view toggle" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/8e76b3f30b1caaba.png" />
