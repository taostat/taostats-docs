---
title: Subnet Metagraph Data
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
There are a couple of different ways to interact with a Subnet's metagraph

# metagraph column data

There is a capital letter property that extracts each column of the metagraph into a tensor.  The index of the ensor is the UID

```python
import bittensor as bt

#initialize subnet for load data from subnet 18
subnet_number = 18
subnet = bt.metagraph( netuid = subnet_number, lite = False)
#stake for all UIDs
subnet_stake = subnet.S
#incentive for all UIDs
subnet_incentive = subnet.I
#Emission for all UIDs
subnet_emission = subnet.E
#Dividends for all UIDs
subnet_dividends = subnet.D
#Weights for all UIDs
subnet_weights = subnet.W
#Trust for all UIDs
subnet_trust = subnet.T
#Vtrust for all UIDs
subnet_vtrust =subnet.Tv
#Coldkeys for all UIDs
subnet_coldkeys = subnet.coldkeys
#hotkeys
subnet_hotkeys = subnet.hotkeys
#ip address
subnet_IPs = subnet.addresses
```

With this data, you can parse specific data for a UID:

Here we print the Incentive, Consensus, Trust and coldkey for the miner in UID 191:

```python
miner_uid =191 

print(subnet.I[miner_uid].item())
print(subnet.C[miner_uid].item())
print(subnet.T[miner_uid].item())
print(subnet.coldkeys[miner_uid])

0.002563515678048134
0.0024872205685824156
0.851819634437561
5DttuDH5FoKhDE4naudtBhzGC4XtwNAtfRN6NMN6woqgM7NY
```

Get UIDs of miners that share a coldkey:

```python

ck = '5DttuDH5FoKhDE4naudtBhzGC4XtwNAtfRN6NMN6woqgM7NY'
our_miners = []
counter = 0


for coldkey in subnet_coldkeys:
    if coldkey ==ck:
        our_miners.append(counter)
    counter +=1
print(our_miners)

[3, 26, 59, 67, 98, 168, 172, 191, 201, 207, 213, 221]
```

# Metagraph Row data

Another way to access the metagraph information (as rows):

```python
import bittensor as bt  
sub = bt.subtensor( network = 'finney' )
neuron= sub.neuron_for_uid(uid=112, netuid=13)  
print(neuron)

NeuronInfo(hotkey='5GgJNSGW7w4UTzRwN5fj8DoDVASQB5eqAwZdqiQehGxKkdCJ', coldkey='5EJ5tZCqzrE2LRh1Wnjh3HUkrDpkTLuApPDzvVRWvECZiLiK', uid=112, netuid=3, active=False, stake=τ0.365500259, stake_dict={'5EJ5tZCqzrE2LRh1Wnjh3HUkrDpkTLuApPDzvVRWvECZiLiK': τ0.365500259}, total_stake=τ0.365500259, rank=0.004257267109178301, emission=0.020831923, incentive=0.004257267109178301, consensus=0.0038757915617608912, trust=0.7679102769512475, validator_trust=0.0, dividends=0.0, last_update=2687685, validator_permit=False, weights=[], bonds=[], pruning_score=1016, prometheus_info=PrometheusInfo(block=0, version=0, ip='0.0.0.0', port=0, ip_type=0), axon_info=AxonInfo( /ipv0/0.0.0.0:0, 5GgJNSGW7w4UTzRwN5fj8DoDVASQB5eqAwZdqiQehGxKkdCJ, 5EJ5tZCqzrE2LRh1Wnjh3HUkrDpkTLuApPDzvVRWvECZiLiK, 0 ), is_null=False)
```