---
title: List of Events
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
The full list of events can be found in the [Bittensor source code](https://github.com/opentensor/subtensor/blob/main/pallets/subtensor/src/lib.rs#L819) 

```
    NetworkAdded(u16, u16), // --- Event created when a new network is added.
    NetworkRemoved(u16),    // --- Event created when a network is removed.
    StakeAdded(T::AccountId, u64), // --- Event created when stake has been transfered from the a coldkey account onto the hotkey staking account.
    StakeRemoved(T::AccountId, u64), // --- Event created when stake has been removed from the hotkey staking account onto the coldkey account.
    WeightsSet(u16, u16), // ---- Event created when a caller successfully sets their weights on a subnetwork.
    NeuronRegistered(u16, u16, T::AccountId), // --- Event created when a new neuron account has been registered to the chain.
    BulkNeuronsRegistered(u16, u16), // --- Event created when multiple uids have been concurrently registered.
    BulkBalancesSet(u16, u16),       // --- FIXME: Not used yet
    MaxAllowedUidsSet(u16, u16), // --- Event created when max allowed uids has been set for a subnetwork.
    MaxWeightLimitSet(u16, u16), // --- Event created when the max weight limit has been set for a subnetwork.
    DifficultySet(u16, u64), // --- Event created when the difficulty has been set for a subnet.
    AdjustmentIntervalSet(u16, u16), // --- Event created when the adjustment interval is set for a subnet.
    RegistrationPerIntervalSet(u16, u16), // --- Event created when registeration per interval is set for a subnet.
    MaxRegistrationsPerBlockSet(u16, u16), // --- Event created when we set max registrations per block.
    ActivityCutoffSet(u16, u16), // --- Event created when an activity cutoff is set for a subnet.
    RhoSet(u16, u16),            // --- Event created when Rho value is set.
    KappaSet(u16, u16),          // --- Event created when Kappa is set for a subnet.
    MinAllowedWeightSet(u16, u16), // --- Event created when minimun allowed weight is set for a subnet.
    ValidatorPruneLenSet(u16, u64), // --- Event created when the validator pruning length has been set.
    ScalingLawPowerSet(u16, u16), // --- Event created when the scaling law power has been set for a subnet.
    WeightsSetRateLimitSet(u16, u64), // --- Event created when weights set rate limit has been set for a subnet.
    ImmunityPeriodSet(u16, u16), // --- Event created when immunity period is set for a subnet.
    BondsMovingAverageSet(u16, u64), // --- Event created when bonds moving average is set for a subnet.
    MaxAllowedValidatorsSet(u16, u16), // --- Event created when setting the max number of allowed validators on a subnet.
    AxonServed(u16, T::AccountId), // --- Event created when the axon server information is added to the network.
    PrometheusServed(u16, T::AccountId), // --- Event created when the prometheus server information is added to the network.
    EmissionValuesSet(), // --- Event created when emission ratios for all networks is set.
    DelegateAdded(T::AccountId, T::AccountId, u16), // --- Event created to signal that a hotkey has become a delegate.
    DefaultTakeSet(u16), // --- Event created when the default take is set.
    WeightsVersionKeySet(u16, u64), // --- Event created when weights version key is set for a network.
    MinDifficultySet(u16, u64), // --- Event created when setting min difficutly on a network.
    MaxDifficultySet(u16, u64), // --- Event created when setting max difficutly on a network.
    ServingRateLimitSet(u16, u64), // --- Event created when setting the prometheus serving rate limit.
    BurnSet(u16, u64),             // --- Event created when setting burn on a network.
    MaxBurnSet(u16, u64),          // --- Event created when setting max burn on a network.
    MinBurnSet(u16, u64),          // --- Event created when setting min burn on a network.
    TxRateLimitSet(u64),           // --- Event created when setting the transaction rate limit.
    Sudid(DispatchResult),         // --- Event created when a sudo call is done.
    RegistrationAllowed(u16, bool), // --- Event created when registration is allowed/disallowed for a subnet.
    PowRegistrationAllowed(u16, bool), // --- Event created when POW registration is allowed/disallowed for a subnet.
    TempoSet(u16, u16),                // --- Event created when setting tempo on a network
    RAORecycledForRegistrationSet(u16, u64), // Event created when setting the RAO recycled for registration.
    WeightsMinStake(u64), // --- Event created when min stake is set for validators to set weights.
    SenateRequiredStakePercentSet(u64), // Event created when setting the minimum required stake amount for senate registration.
    AdjustmentAlphaSet(u16, u64), // Event created when setting the adjustment alpha on a subnet.
    Faucet(T::AccountId, u64),    // Event created when the facuet it called on the test net.
    SubnetOwnerCutSet(u16),       // Event created when the subnet owner cut is set.
    NetworkRateLimitSet(u64),     // Event created when the network creation rate limit is set.
    NetworkImmunityPeriodSet(u64), // Event created when the network immunity period is set.
    NetworkMinLockCostSet(u64),   // Event created when the network minimum locking cost is set.
    SubnetLimitSet(u16),          // Event created when the maximum number of subnets is set
    NetworkLockCostReductionIntervalSet(u64), // Event created when the lock cost reduction is set
    HotkeySwapped {
        coldkey: T::AccountId,
        old_hotkey: T::AccountId,
        new_hotkey: T::AccountId,
    }, // Event created when a hotkey is swapped
```
