---
title: Alpha:
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

List of commonly used terms in Bittensor and on Taostats.

Each subnet has a token corresponding to its symbol (alpha, beta, delta....). To generalise subnet tokens, they are referred to as alpha.

Note [Liquid Alpha](#liquid-alpha) is a different term.

# Alpha in (aka Alpha pool, Alpha Reserve)

The amount of alpha that is present in the liquidity pool. Depending on the context, this can also refer to the amount of alpha being added to a pool during a block.

# Alpha out (aka Alpha outstanding, alpha staked)

The amount of alpha that has been staked onto hotkeys. Alpha\_out can refer to *all* of the alpha staked, or to the alpha being staked to a specific wallet. Examples: Subnet 37 has 4,000 alpha out. I have 100 alpha out staked from subnet 16.

Alpha\_out can also refer to the amount of alpha being added to the hotkeys during a block.

# Alpha Price:

This is defined by the ratio of tao\_in/alpha\_in ... the assets in the liquidity pool.

# Bittensor:

The peer-to-peer network for open machine intelligence. Bittensor is composed of independent subnets, each running its own incentive mechanism, connected through the [subtensor](#subtensor) chain. Nodes on subnets earn [tao](#tao) for producing work that other nodes rate as valuable. See [bittensor.com](https://bittensor.com/) for the whitepaper and network overview.

# Burn:

The permanent removal of tao from circulation. Burn is distinct from [recycle](#recycle): recycled tao re-enters the emission pool at a later date, whereas burned tao is destroyed. On Bittensor, "burn" in most registration and UI contexts actually means **recycle** — the tao is removed from circulation and re-emitted later, not destroyed. Transaction fees, for example, are recycled rather than permanently burned. See [Burning](/docs/burning).

# Child hotkey (Childkey):

A hotkey that receives delegated stake authority from a [parent hotkey](#parent-hotkey). The parent keeps custody of the coldkey and stake; the child registers on subnets and runs validator or miner workloads. Enables split of custody and operation. See [Emission for Parent/Child Hotkeys](/docs/emission-parent-hotkeys).

# Coldkey:

The main key for a Bittensor wallet. It holds your funds and authorises transfers, purchases, sales, and staking/delegation. Because it can be kept offline (cold storage) and is only needed to sign fund-moving transactions, it is the security root of the wallet — losing or exposing it puts your balance at risk.

# Coldkey swap:

The process of transferring all state on a [coldkey](#coldkey) (balances, stakes, delegations) to a new coldkey. Initiated on-chain with a delay period before it finalises, to prevent theft via a compromised hot session. The pending swap is queryable via the pending-coldkey-swap API. See [Pending Coldkey Swap API](/api-reference/pending-coldkey-swap/).

# Commit Reveal:

Bittensor's approach to address [weight copying](#weight-copying). A process where validators encrypt their weights for a given period, preventing weight copiers from reading their weights immediately.

# Consensus:

Miner's score from the Yuma Consensus. Not applicable to validators.

# Consensus based weights:

See [liquid alpha](#liquid-alpha)

# Conviction:

A governance-vote weighting mechanism where locking tao for longer periods amplifies vote weight. Longer conviction locks give more influence over proposals. Conviction v2 refined the multipliers and lock schedule. See [Conviction v2](/docs/conviction-v2).

# Daily Rewards:

A column in the subnet metagraph. Based on the current emission, extrapolated to 24 hours. Example: If your emission is 1 alpha/epoch, your Daily reward will be 20 alpha. (20 epochs/day)

# Delegate:

The verb form: to stake tao to a validator's [hotkey](#hotkey), creating a [delegation](#delegation) relationship. When tao is delegated, the owner of the tao receives a portion of the validator's emissions minus the validator's [take](#take). See [Delegation](/docs/delegation).

# Delegation:

The standing relationship in which a tao owner assigns stake to a validator's [hotkey](#hotkey). The delegator retains ownership via their [coldkey](#coldkey), the validator uses the stake weight for consensus, and the delegator earns a share of emissions minus the validator's [take](#take). "Delegate" (verb) is the act of creating this relationship; "delegation" is the relationship itself. See [Delegation](/docs/delegation).

# Deregistration:

Removal of a neuron from a subnet's [metagraph](#metagraph), freeing its slot for a new registration. Neuron deregistration occurs when a neuron with expired [immunity](#immunity) ranks lowest by incentive. Subnet deregistration can also occur, removing an entire subnet from the network. The deregistration ranking endpoint exposes the pending neuron order. See [Neuron Deregistration API](/api-reference/subnet/get-api-subnet-neuron-deregistration-v1).

# Dividends:

A score for validators denoting the fraction of emission for each validator.

# dTao:

The dynamic-tao protocol upgrade, activated February 2025, that replaced the root-subnet-weighted emission model with per-subnet automated market makers. Each subnet now has its own [alpha](#alpha) token traded against tao in a [liquidity pool](#liquidity-poolsubnet-pool), and emissions flow via pool activity rather than root-subnet weights. See [Subnet Mechanisms](/docs/subnet-mechanisms).

# Emission:

Emission describes the distribution of tao or [alpha](#alpha) in the network. Emission shows up in three contexts:

* **Subnet Emission**: the share of network tao that flows to each subnet. For example a 10% emission means that 10% of all tao generated is sent to that subnet. As of spec 440, this share is not a pure pro-rata of pool demand: an [emission gate](/docs/emission-gate) redistributes emission from the low-demand tail to the above-bar winners.
* **Neuron Emission**: inside each subnet, all miners and validators are awarded emission (as seen in the [metagraph](#metagraph)). Neuron emission is denominated in the subnet's [alpha](#alpha) per [epoch](#epoch).
* **Alpha Emission**: the per-block issuance of a subnet's [alpha](#alpha) token, split between the pool, hotkeys, and the subnet owner per the subnet mechanism.

When a subnet closes registration, it retains its emission percentage, but all tao is [recycled](#recycle), so miners and validators receive no emission.

# Epoch:

A single cycle of the subnet [tempo](#tempo), during which validators set weights and emissions are distributed. Default tempo is 360 blocks, so an epoch is roughly 72 minutes at 12-second blocks. Rewards, [daily rewards](#daily-rewards) math, and Yuma consensus all key off epoch boundaries.

# Events:

Chain records emitted when an [extrinsic](#extrinsic) executes. Events cover registrations, stake additions/removals, delegations, transfers, weight commits, and governance actions. Taostats indexes chain events and exposes them via the events API. See [Events Detail](/docs/events-detail).

# Exchange rate:

This is defined by the ratio of tao\_in/alpha\_in ... the assets in the liquidity pool. Also known as [alpha price](#alpha-price).

# Extrinsic:

A transaction submitted to the [subtensor](#subtensor) chain. Extrinsics wrap one or more chain calls, are optionally signed by a [coldkey](#coldkey) or [hotkey](#hotkey), and produce [events](#events) when executed. Common examples: `Balances.transfer`, `SubtensorModule.add_stake`, `SubtensorModule.register_neuron`. See [Extrinsics and Events](/docs/extrinsics-and-events).

# Finalized:

A block that has passed GRANDPA finality and can no longer be reverted. Distinct from "best block", which is the current head of the chain and may still reorganise. Taostats API responses generally reflect finalized state.

# Halving/Halvening:

When half of the remaining supply has been issued, the block reward drops by half. The first tao halving occurred in **December 2025**, when 10,500,000 tao had been issued; the block reward fell from 1 tao/block to 0.5 tao/block. Tao and alpha halve on independent schedules. See [Halving](/docs/halving).

# Hotkey:

Hotkeys are used to register subnets and nodes on the network. One hotkey can be registered per subnet. All hotkeys are associated with a coldkey, and a coldkey can have multiple hotkeys. The hotkey is the operational, online key — it signs the frequent network operations a running validator or miner performs, so it is kept accessible (hot). It cannot move the coldkey's funds, which limits the damage if it is compromised.

# Hyperparameter(s):

Per-subnet tunable parameters that govern subnet behaviour: tempo length, immunity period, minimum stake, weights-set rate limit, liquid-alpha toggle, and dozens more. Set by the subnet owner via `sudo_set_hyperparameter` extrinsics. See [Subnet Parameters](/docs/subnet-parameters).

# Identity:

On-chain identity records associated with a [coldkey](#coldkey), [hotkey](#hotkey), or subnet. Stores display name, website, description, and other metadata via the Identities storage in the SubtensorModule [pallet](#pallet). Surfaced across the API in owner and subnet responses.

# Immunity:

Time period (defined in blocks) that a new node or subnet is protected from de-registration.

# Incentive:

A score for miners. Calculated from consensus, the incentive denotes the portion of miner emissions to be distributed to each miner.

# Liquid Alpha:

Also known as consensus based weights. Introduced in Bittensor 7.3, this feature changes the way Validator dividends are calculated. The "Bond" between each validator and miner is an exponential moving average, where the most recent bond is weighted at alpha = 0.9. With Liquid alpha, this becomes a variable. Subnets with Liquid alpha enabled set the [Subnet Hyperparameters](/docs/subnet-parameters) `liquid_alpha_enabled` to true.

# Liquidity pool/Subnet pool:

Each subnet will have a liquidity pool where tao can be exchanged for alpha. The ratio of tao/alpha in the liquidity pool defines the tao/alpha exchange rate.

# MCP (Model Context Protocol):

An open standard for exposing tools and data to language models. Taostats runs an MCP server that lets LLM clients query subnet, neuron, price, and extrinsic data through structured tool calls. See [Model Context Protocol (MCP)](/docs/mcp-guide).

# Mechanism (subnet mechanism):

A sub-subnet primitive introduced with [dTao](#dtao). A subnet owner can partition emissions and validation across multiple mechanisms inside the same subnet, each with its own scoring rules. Enables specialisation without registering a new subnet. See [Subnet Mechanisms](/docs/subnet-mechanisms).

# Metagraph:

The canonical per-subnet view of neurons and their scores at a given block. Contains one row per registered [neuron](#neuron) with columns for stake, incentive, dividends, trust, [vtrust](#vtrust), emission, and daily rewards. Taostats exposes the metagraph as an API endpoint and as a UI chart. See [Metagraph](/docs/metagraph).

# MEV / MEV shield:

Maximal extractable value: profit a block producer can capture by reordering or inserting transactions. Bittensor's MEV shield uses [commit reveal](#commit-reveal) and other primitives to keep validator weights hidden from potential extractors until after execution. See [MEV Shield](/docs/mev-shield).

# Miner:

Miners are nodes on a subnet. Miners are given work to perform, and this work is graded by the validators. Miners receive alpha emissions (the subnet's token) as an incentive for their work. [Miner](/docs/miner)

# Moving average:

A time-weighted average used in several Bittensor metrics. Notable uses: the bond exponential moving average in [Liquid Alpha](#liquid-alpha), and smoothed daily-reward projections in the metagraph. Not a standalone chain concept.

# Multisig:

A Substrate extrinsic pattern where a call requires signatures from M of N cosigners before it executes. Used for treasuries, subnet governance, and joint custody of large coldkey balances. Follows the standard Substrate multisig [pallet](#pallet) semantics. See [Multisig Extrinsics](/docs/multisig-extrinsics).

# Netuid:

The u16 identifier of a subnet on the [subtensor](#subtensor) chain. Every API endpoint that operates on a subnet takes `netuid` as its primary key. Netuid 0 is the [root subnet](#root-subnet). See [Subnets](/docs/subnets) and the [Subnet API](/api-reference/subnet/).

# Neuron:

A registered participant in a subnet, either a [validator](#validator) or a [miner](#miner). "Neuron" is the generic term when the validator/miner distinction does not matter, e.g. in the [metagraph](#metagraph) or in registration counts. Also referred to as "node" in some older docs. See the [Neuron API](/api-reference/neuron/).

# Nominator:

An alias for a delegator (see [Delegation](#delegation)) used in the "Calculating Nominator Returns" doc and in some Substrate contexts. Same on-chain relationship: tao owner assigning stake weight to a validator. Prefer "delegator" in new writing; keep "nominator" only when referencing existing docs or Substrate primitives.

# On-chain:

State that lives in the [subtensor](#subtensor) chain database and is settled by consensus. Contrasted with off-chain data (indexer views, API-side analytics, cached snapshots). If an answer changes based on which subtensor RPC you query, it is on-chain; if it comes from Taostats' indexer only, it is not.

# OTC:

The over-the-counter alpha marketplace on Taostats, where traders can execute alpha-token trades outside the on-chain AMM. Useful for size trades that would incur unacceptable [slippage](#slippage) against a subnet [liquidity pool](#liquidity-poolsubnet-pool). See the [OTC API](/api-reference/otc/).

# Pallet:

A Substrate module that packages related storage, extrinsics, and events. Bittensor's core logic lives in the `SubtensorModule` pallet, with supporting pallets for balances, staking, governance, and multisig. Extrinsic paths are namespaced by pallet, e.g. `SubtensorModule.register_neuron`.

# Parent hotkey:

A [hotkey](#hotkey) that delegates registration and validation authority to one or more [child hotkeys](#child-hotkey-childkey). The parent keeps stake; the child does the work. Used to separate long-lived stake custody from short-lived operational keys. See [Child & Parent Hotkeys](/docs/child-hotkeys).

# Price impact:

The change in a subnet AMM's effective price caused by a single trade, expressed as a percentage of the pre-trade price. Larger trades against smaller pools produce larger price impact. Distinct from [slippage](#slippage), which measures the gap between expected and realised price for a specific order. See [Slippage](/docs/slippage).

# Proxy:

A Substrate extrinsic pattern where one account calls on behalf of another via a delegated permission. Bittensor supports proxy for stake operations and governance votes, letting a "hot" operational account act for a "cold" ownership account without exposing coldkey signatures. See [Proxy Extrinsics](/docs/proxy-extrinsics).

# Rao:

The smallest denomination of [tao](#tao). One tao equals 10^9 rao. API responses that need integer precision typically report values in rao and let clients divide by 1e9 for display.

# Recycle:

Tao that is recycled is removed from circulation to be emitted again at a later date. As tao is recycled, the chain [halving](#halvinghalvening) is pushed to a later time. See [Recycling](/docs/recycling).

# Root subnet:

Subnet 0. Pre-[dTao](#dtao), root held the weighted vote that determined per-subnet emission shares. Post-dTao, root still exists for chain governance and legacy compatibility, but subnet emissions are driven by [liquidity pool](#liquidity-poolsubnet-pool) activity rather than root voting. See [Stakeholder Emissions: Root](/docs/stakeholder-emissions-root).

# Runtime:

The Substrate runtime: the state-transition logic of the [subtensor](#subtensor) chain, versioned via `runtime_version`. Runtime upgrades ship as chain forkless updates that all nodes adopt automatically. [Extrinsic](#extrinsic) and [event](#events) schemas are pinned to runtime versions.

# Senate:

Bittensor's governance body, composed of the top-k validators by stake. The senate votes on proposals routed through the governance flow and can veto or approve chain changes. See [Senate](/docs/senate).

# Signature:

A cryptographic signature (typically sr25519 or ed25519) that authorises a chain [extrinsic](#extrinsic). Produced by signing the encoded call with a [coldkey](#coldkey) or [hotkey](#hotkey). Wallets, browser extensions, and CLI tools all wrap this signing step.

# Slippage:

The gap between the price a trader expects and the price they actually receive on an AMM trade. Slippage is inversely related to [liquidity pool](#liquidity-poolsubnet-pool) depth: the shallower the pool, the larger the slippage for the same trade size. See [Slippage](/docs/slippage).

# SS58:

The Substrate address encoding format used across Polkadot, Kusama, and Bittensor. An SS58 address is a base58-encoded public key with a network prefix byte and a checksum. Every wallet, coldkey, hotkey, and API sample in these docs uses SS58 strings. See the [SS58 spec](https://github.com/paritytech/ss58-registry).

# Stake:

A tao owner can stake (or delegate) their tao with a validator. The higher the validator's stake, the higher their return. Post-dTAO, delegated tao receives a portion of the subnet's alpha emissions (not TAO). See: [Delegation](/docs/delegation) and [Staking in dTao](/docs/staking-in-dtao).

# Substrate:

The blockchain framework, maintained by Parity, that Bittensor's [subtensor](#subtensor) chain is built on. Substrate provides the runtime, consensus (BABE + GRANDPA), extrinsic model, and [pallet](#pallet) system. See [substrate.io](https://substrate.io/).

# Subnet:

Short for "subnetwork." Bittensor is made up of many subnets, each with its own purpose, token, and emissions; the count changes as subnets register and deregister — see the [live list on taostats.io/subnets](https://taostats.io/subnets). [Subnets](/docs/subnets).

# Subtensor:

The reference implementation of the Bittensor chain: the node software and runtime. "Subtensor" refers to the chain and its codebase; "Bittensor" refers to the broader network and its economic protocol. The two are commonly conflated but are distinct. See the [subtensor repo](https://github.com/opentensor/subtensor).

# Sudo:

A Substrate [pallet](#pallet) that grants a designated key privileged authority to execute otherwise-restricted extrinsics, typically used for governance and hyperparameter changes. On Bittensor, sudo calls originate from the governance flow, not from an individual account.

# Take:

The percentage of validator emissions kept by the validator. The remaining percentage is distributed amongst delegators. This is a variable that is set by each validator. It can range from 0-18% (default 18%) and can be updated once every 30 days.

# Tao:

The token of the Bittensor [subtensor](#subtensor). Since the December 2025 [halving](#halvinghalvening), 0.5 tao is emitted per block (12-second blocks). Tao can be divided into [rao](#rao) (there are 1B rao per tao). Learn more about [Tao](/docs/tao) and [Tao Emission](/docs/tao-emission).

# tao in:

The tao in the subnet liquidity pool. It can also refer to the amount of tao being added to the pool in each block.

# Tempo:

The subnet parameter that sets how many blocks pass between weight-set windows and emission distributions. Default is 360 blocks, roughly 72 minutes at 12-second blocks. One tempo cycle is one [epoch](#epoch).

# Trust:

A score for miners, created by the Yuma Consensus. It is a combination of all the weights from all the validators. Higher trust leads to higher incentive & emissions.

# Undelegate:

The process of removing delegation/stake from a validator. The tao removed from the validator will be added to the user's coldkey.

# Unstake:

The inverse of [stake](#stake): remove tao (or alpha) from a hotkey and return it to the coldkey balance. Executed via `SubtensorModule.remove_stake`. Unstaking is subject to per-subnet rules and may involve unbonding delays on some flows.

# Validator:

Validators are nodes on a subnet. Validators check the work of the miners and grade the miners based on the quality of the response. [Validator](/docs/validator)

# VTrust:

A score given to validators on a subnet. It is a ranking based on how well the validator's weights match the consensus. High VTrust leads to higher emissions.

# Weight copying:

When a validator copies the weights of other validators. This is sometimes done to avoid grading the miners, and thus not providing value to the Subnet.
