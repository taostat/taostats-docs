---
title: Error Codes
excerpt: When working on chain there are error messages. What do they mean?
deprecated: false
hidden: false
metadata:
  robots: index
---
```
CustomTransactionError::ColdkeyInSwapSchedule => 0,\
CustomTransactionError::StakeAmountTooLow => 1,
CustomTransactionError::BalanceTooLow => 2,
CustomTransactionError::SubnetDoesntExist => 3,
CustomTransactionError::HotkeyAccountDoesntExist => 4,
CustomTransactionError::NotEnoughStakeToWithdraw => 5,
CustomTransactionError::RateLimitExceeded => 6,
CustomTransactionError::InsufficientLiquidity => 7,
CustomTransactionError::SlippageTooHigh => 8,
CustomTransactionError::TransferDisallowed => 9,
CustomTransactionError::HotKeyNotRegisteredInNetwork => 10,
CustomTransactionError::InvalidIpAddress => 11,
CustomTransactionError::ServingRateLimitExceeded => 12,
CustomTransactionError::InvalidPort => 13,
CustomTransactionError::BadRequest => 255,
CustomTransactionError::ZeroMaxAmount => 14,
```

<br />

## Error Code 0. ColdKeyInSwapSchedule

Description: Your coldkey is set to be swapped. No transfer operations are possible.

## Error Code 1 StakeAmountTooLow

Description: The amount you are staking/unstaking/moving is below the minimum TAO equivalent.\
Minimum: 500,000 RAO (0.0005 TAO)

## Error Code 2  BalanceTooLow

Description: The amount of stake you have is less than you have requested.

## Error Code 3 SubnetDoesntExist

Description: This subnet does not exist.

## Error Code 4 HotkeyAccountDoesntExist

Description: Hotkey is not registered on Bittensor network.

## Error Code 5  NotEnoughStakeToWithdraw

Description: You do not have enough TAO equivalent stake to remove/move/transfer, including the unstake fee.

## Error Code 6  RateLimitExceeded

Description: Too many transactions submitted (other than Axon serve/publish extrinsic).

## Error Code 7 InsufficientLiquidity

Description: The subnet's pool does not have sufficient liquidity for this transaction.

## Error Code 8 SlippageTooHigh

Description: The slippage exceeds your limit. Try reducing the transaction amount.

## Error Code 9 TransferDisallowed

Description: This subnet does not allow stake transfer.

## Error Code 10  HotKeyNotRegisteredInNetwork

Description: The hotkey is not registered in the selected subnet.

## Error Code 11 InvalidIpAddress

Description: Axon connection info cannot be parsed into a valid IP address.

## Error Code 12  ServingRateLimitExceeded

Description: Rate limit exceeded for axon serve/publish extrinsic.

## Error Code 13 InvalidPort

Description: Axon connection info cannot be parsed into a valid port.

## Error Code 14 ZeroMaxAmount

Description: The executable amount must be greater than zero.

## Error Code 255 BadRequest

Description: Unclassified error.