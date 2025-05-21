---
title: Miner Report
excerpt: A jupyter Notebook to collect neuron registration information
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
This [Jupyter Notebook](https://github.com/taostat/awesome-taostats-api-examples/blob/main/python/miner_report.ipynb) takes an array of Coldkeys, finds every neuron registration, and generates a report.

In Cells 1&2 of the notebook, insert your api key, and the Coldkeys you wish to examine:

<br />

```python
api_key = ""
coldkeys =[]
```

Cells 3&4 are functions to help with hex-> SS58 address conversion and a datetime fixer.

Cell 5:

Our first API call - loops through the extrinsics API until we have retrieved every extrinsic for your coldkeys.  If you have fairly prolific cokdkeys, you may want to add a time.sleep here to avoid getting rate limited.

All extrinsics are now saved in `all_extrinsics`.

cell 6 : Calculates the number of extrinsics

Cell 7: Used to see formatting of the various calls that might be made for a miner.

Cell 8:  

Collect data on neuron registrations:

- Loop through all the extrinsics.  If there is a registration AND it was successful
- Find the next de-registration event for the hotkey. Now we can find how long the hotkey was registered on the network.
- Find how much the registration cost was (from the events)
- Find the price at the time of registration.
  - With the cost in tao, and the price in $$, we know how much expense was made to register the neuron.
- Add a sleep to avoid getting rate limited

From this cell we have a lot of data about our miner/validator registrations.

We can make charts, find average times of registration, and sum up all the costs.