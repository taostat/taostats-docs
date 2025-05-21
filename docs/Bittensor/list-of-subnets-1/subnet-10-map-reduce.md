---
title: 'Subnet 10 (kappa): Map Reduce/taomap'
excerpt: This page last updated March 28, 2024
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
The Bittensor Subnet 10 (Map Reduce Subnet) incentivizes miners by offering rewards for contributing network bandwidth and memory resources.

A broadcast subnet leverages the bandwidth of multiple peers to transfer large data from point to A to multiple point Bs without needing to leverage large quantities of your own upload. The concept is simple, a large file D can be split into multiple chunks and sent to N intermediate peers (usually with redundancy) and then forwarded onward to B additional endpoints in an N by B full bipartite fashion. The inverse operation is also valuable, where data DxB large data files can be aggregated from B peers by leveraging the bandwidth of N intermediaries.

In the forward 'map' operation a file D is broken into chunks and split across the N peers each of whom then forwards their chunk to B endpoints allowing each downloading peer to recieve the full file of size D with the sending peer needing an upload of only size D. The backward operation, 'reduce', acts in reverse, the K receiving peers fan out their response data D in chunks to the N intermediary peers who then aggregate the chunks from each other and finally send the sum of total chunks back to the sending peer A.

The map-reduce cycle is essential for reducing the bandwidth by a factor of K on the running peers which is essential for the training of machine learning models in a distributed setting. This template is a protoype for incentivizing the speed at which this operation can take place by validating both the consistency and operation speed of a map-reduce.

# [GitHub](https://github.com/dream-well/map-reduce-subnet)

# [Frontend](https://taomap.ai/)

# HW Requirements:

## [Miner](#running-miner)

## [Validator](#running-validator)
