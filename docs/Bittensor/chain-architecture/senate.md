---
title: Senate
excerpt: The Bittensor Senate can vote on proposed changes to the chain.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
The Senate consists of a body of elected representatives who hold a substantial share of the network's total stake.

Network participants who have allocated their stake to any Senate member are represented by the chosen delegate's party. This system ensures that every stakeholder can have their voice heard by delegating their stake to representatives that align with their views.

## Eligibility Criteria

To be eligible for Senate participation, a member must satisfy the following four criteria. A coldkey-hotkey pair can only cast votes on proposals once these conditions are met.

* Is registered as a hotkey-coldkey pair with a sub-network.
* Has put themselves forward as a delegate for staking their $TAO.
* Possesses a hotkey stake exceeding 2% of the total network stake, either through direct staking or delegation.
* Has opted to be part of the Senate.

A coldkey-hotkey pair is entitled to vote on any proposal put forth by the Triumvirate once they meet these requirements.

If the Senate's twelve seats are occupied, and another delegate seeks entry, they may take the place of the member with the least stake, provided they hold a larger stake.

## Entering the Senate

Delegates may opt into the Senate by executing the following command:

`btcli root register`

This is contingent on fulfilling all the prerequisites outlined in the Eligibility Criteria section above.

Upon running the command and its inclusion in a block, delegates can verify their Senate membership with:

`btcli root list`

## Casting Votes

Delegates in the Senate are empowered to cast votes on ongoing proposals within the designated timeframe, from the proposal's initiation to its conclusion. Absence from a vote equates to a vote against the proposal.

To vote, a delegate uses :

`btcli root proposals`

then:

* Retrieve the proposal hash from the summary.
* Executes `btcli root senate_vote` and inputs the proposal hash, either with the `--proposal` flag or when the command prompts for the proposal hash.
* Subsequently, they will be prompted to choose between approval or disapproval. Once the choice is confirmed, the vote is recorded in the upcoming block and tallied. This can be verified using `btcli root proposals`.