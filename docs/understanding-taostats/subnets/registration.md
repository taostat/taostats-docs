---
title: Registration Data
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

Taostats subnet registration charts can be found on each Subnet page under the **Registration** tab.

There are three sections to this page:

A historical chart of the cost in tao to register a node on the subnet.  To the right of the chart is the current registration cost:

In the screenshot, the current registration cost is 0.06 tao. Registration rates vary by the competitiveness of the subnet.

<Image border={false} alt="Taostats subnet registration data view combining a current-cost stat pill with a time-series area chart of registration cost in TAO and a range selector" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/edc44802986dd6d0.png" />

# Immune Miners

A daily tally of how many miners were immune at midnight GMT.

<Image border={false} alt="Taostats subnet immune miner bar chart plotting daily immune count over time with a range selector" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/44b3dff2618a2092.png" />

# Registration Table

This table lists the hotkeys and coldkeys of every neuron registration in the subnet. A key value for miners is how many registration occurred in the last 24 hours - this is an indicator of the cutoff for the *next* 24 hours.

<Image border={false} alt="Taostats subnet registration table with UID, hotkey, coldkey, time, and block columns plus filter, CSV export, and rows selector" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/1bdfe09a5a1ebbcd.png" />
