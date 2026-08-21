---
title: Extrinsics: proxy
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

Proxies are wallets that are authorized by other wallets to perform tasks.  There are several proxy types on Bittensor, each with different permissions

> 📘 **Securing your wallet**
>
> For how proxies fit into an overall wallet-security setup alongside ledgers and multisig, see [Securing a wallet: ledgers, multisig & proxies](/docs/securing-a-wallet).

## ✅ ProxyType Permission Table

| ProxyType                  | Transfer Funds | Stake Tokens | Register | Govern | Admin (Sudo)              | Non-Critical Calls | Full Access        |
| -------------------------- | -------------- | ------------ | -------- | ------ | ------------------------- | ------------------ | ------------------ |
| **Any**                    | ✅              | ✅            | ✅        | ✅      | ✅                         | ✅                  | ✅                  |
| **NonTransfer**            | ❌              | ✅            | ✅        | ✅      | ✅                         | ✅                  | ❌                  |
| **NonFungible**            | ❌              | ❌            | ❌        | ✅      | ✅                         | ✅                  | ❌                  |
| **Transfer**               | ✅              | ❌            | ❌        | ❌      | ❌                         | ❌                  | ❌                  |
| **SmallTransfer**          | ✅ *(\< limit)* | ❌            | ❌        | ❌      | ❌                         | ❌                  | ❌                  |
| **Owner**                  | ❌              | ❌            | ❌        | ✅      | ❌ *(no sudo override)*    | ✅                  | ❌                  |
| **NonCritical**            | ✅              | ✅            | ✅        | ✅      | ❌ *(no sudo or dissolve)* | ✅                  | ❌                  |
| **Triumvirate**            | ❌              | ❌            | ❌        | ✅      | ❌                         | ❌                  | ❌                  |
| **Senate**                 | ❌              | ❌            | ❌        | ✅      | ❌                         | ❌                  | ❌                  |
| **Governance**             | ❌              | ❌            | ❌        | ✅      | ❌                         | ❌                  | ❌                  |
| **Staking**                | ❌              | ✅            | ❌        | ❌      | ❌                         | ❌                  | ❌                  |
| **Registration**           | ❌              | ❌            | ✅        | ❌      | ❌                         | ❌                  | ❌                  |
| **RootWeights**            | ❌              | ❌            | ❌        | ❌      | ❌                         | ❌                  | ✅ *(weights only)* |
| **ChildKeys**              | ❌              | ❌            | ❌        | ❌      | ❌                         | ✅ *(child ops)*    | ❌                  |
| **SudoUncheckedSetCode**   | ❌              | ❌            | ❌        | ❌      | ✅ *(set\_code only)*      | ❌                  | ❌                  |
| **SwapHotkey**             | ❌              | ❌            | ❌        | ❌      | ❌                         | ✅ *(swap hotkey)*  | ❌                  |
| **SubnetLeaseBeneficiary** | ❌              | ❌            | ❌        | ❌      | ✅ *(admin utils only)*    | ❌                  | ❌                  |

## 💡 What the Columns Mean:

Transfer Funds: Can do balance or transfer\_stake calls.

Stake Tokens: Can add\_stake, remove\_stake, etc.

Register: Can call register, burned\_register, root\_register.

Govern: Can interact with Senate, Triumvirate, governance calls.

Admin (Sudo): Has access to Sudo or sudo-like functions.

Non-Critical Calls: Can do things that aren't dangerous or destructive.

Full Access: Implies general-purpose, including sensitive actions.

📝 Notes

SmallTransfer is a subset of Transfer, with a limit.

Governance includes both Senate and Triumvirate.

NonCritical blocks very sensitive calls (like dissolve\_network, sudo, etc.).

SudoUncheckedSetCode only allows a specific kind of powerful system update.

SubnetLeaseBeneficiary is a specialized admin group for managing serving parameters (difficulty, weight settings, etc.).
