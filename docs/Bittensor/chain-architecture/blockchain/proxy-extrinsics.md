---
title: Proxy Extrinsics
deprecated: false
hidden: false
metadata:
  robots: index
---
Proxies are wallets that are authorized by other wallets to perform tasks.  There are several proxy types on Bittensor, each with different permissions

## ✅ ProxyType Permission Table

| ProxyType                  | Transfer Funds | Stake Tokens | Register | Govern | Admin (Sudo)              | Non-Critical Calls | Full Access        |
| -------------------------- | -------------- | ------------ | -------- | ------ | ------------------------- | ------------------ | ------------------ |
| **Any**                    | ✅              | ✅            | ✅        | ✅      | ✅                         | ✅                  | ✅                  |
| **NonTransfer**            | ❌              | ✅            | ✅        | ✅      | ✅                         | ✅                  | ❌                  |
| **NonFungible**            | ❌              | ❌            | ❌        | ✅      | ✅                         | ✅                  | ❌                  |
| **Transfer**               | ✅              | ❌            | ❌        | ❌      | ❌                         | ❌                  | ❌                  |
| **SmallTransfer**          | ✅ _(\< limit)_ | ❌            | ❌        | ❌      | ❌                         | ❌                  | ❌                  |
| **Owner**                  | ❌              | ❌            | ❌        | ✅      | ❌ _(no sudo override)_    | ✅                  | ❌                  |
| **NonCritical**            | ✅              | ✅            | ✅        | ✅      | ❌ _(no sudo or dissolve)_ | ✅                  | ❌                  |
| **Triumvirate**            | ❌              | ❌            | ❌        | ✅      | ❌                         | ❌                  | ❌                  |
| **Senate**                 | ❌              | ❌            | ❌        | ✅      | ❌                         | ❌                  | ❌                  |
| **Governance**             | ❌              | ❌            | ❌        | ✅      | ❌                         | ❌                  | ❌                  |
| **Staking**                | ❌              | ✅            | ❌        | ❌      | ❌                         | ❌                  | ❌                  |
| **Registration**           | ❌              | ❌            | ✅        | ❌      | ❌                         | ❌                  | ❌                  |
| **RootWeights**            | ❌              | ❌            | ❌        | ❌      | ❌                         | ❌                  | ✅ _(weights only)_ |
| **ChildKeys**              | ❌              | ❌            | ❌        | ❌      | ❌                         | ✅ _(child ops)_    | ❌                  |
| **SudoUncheckedSetCode**   | ❌              | ❌            | ❌        | ❌      | ✅ _(set_code only)_       | ❌                  | ❌                  |
| **SwapHotkey**             | ❌              | ❌            | ❌        | ❌      | ❌                         | ✅ _(swap hotkey)_  | ❌                  |
| **SubnetLeaseBeneficiary** | ❌              | ❌            | ❌        | ❌      | ✅ _(admin utils only)_    | ❌                  | ❌                  |

<br />

## 💡 What the Columns Mean:

Transfer Funds: Can do balance or transfer_stake calls.

Stake Tokens: Can add_stake, remove_stake, etc.

Register: Can call register, burned_register, root_register.

Govern: Can interact with Senate, Triumvirate, governance calls.

Admin (Sudo): Has access to Sudo or sudo-like functions.

Non-Critical Calls: Can do things that aren't dangerous or destructive.

Full Access: Implies general-purpose, including sensitive actions.

📝 Notes

SmallTransfer is a subset of Transfer, with a limit.

Governance includes both Senate and Triumvirate.

NonCritical blocks very sensitive calls (like dissolve_network, sudo, etc.).

SudoUncheckedSetCode only allows a specific kind of powerful system update.

SubnetLeaseBeneficiary is a specialized admin group for managing serving parameters (difficulty, weight settings, etc.).