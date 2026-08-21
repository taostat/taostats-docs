---
title: Bittensor Auth
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

Bittensor Auth is standard OAuth authentication powered by on-chain identity and permissions. It lets any application use Bittensor wallets as identities and on-chain state as access control, through the Taostats Auth Gateway. Learn more at [taostats.io/bittensor-auth](https://taostats.io/bittensor-auth) or test flows at [auth.taostats.io](https://auth.taostats.io).

> 📘 **Works with any OAuth2 or OIDC library** — no custom SDK required. Because it is standard OAuth2/OIDC, it drops into off-the-shelf tools such as Grafana, JupyterHub, Gitea, Nextcloud, FastAPI, and NextAuth.js.

## The problem

Bittensor identity has no standard authentication layer, so today:

- Custom auth gets rebuilt for every subnet.
- OAuth doesn't understand miners or stake.
- Off-the-shelf tools can't authenticate against the chain.
- You can't log in with a browser wallet.

## The solution: OAuth backed by the chain

The Taostats Auth Gateway connects Bittensor identity to the existing OAuth ecosystem:

- **Wallet = Identity**
- **Chain state = Permissions**
- **OAuth = Access token**

## How it works

1. App requests login.
2. Redirect to Taostats Auth.
3. Wallet signs the authentication challenge.
4. On-chain verification.
5. JWT token issued.
6. Application grants access.

> 📘 **Permissions follow the chain automatically.** On-chain scopes are re-verified at every token refresh. If a miner deregisters, their access lapses automatically at the next epoch — no manual revocation.

## On-chain scopes

Scopes verify a condition against on-chain state at authentication and on every refresh:

| Scope | Verifies |
| --- | --- |
| `subnet:1:miner` | Registered miner |
| `subnet:1:validator` | Validator |
| `subnet:18:owner` | Subnet owner |
| `subnet:1:holder:100` | Alpha holder (threshold) |
| `tao:holder:50` | TAO holder (threshold) |
| `delegate:{hotkey}` | Delegator relationship |
| `staker:1000` | Network stake (threshold) |

## Auth flows

| Flow | Use |
| --- | --- |
| **Authorization Code + PKCE** | Standard web application login |
| **Device Code Flow** (RFC 8628) | CLI and headless authentication |
| **OpenID Connect** | Full OIDC compatibility |

## Use cases

- **Headless miner auth** — CLI authentication using Device Code Flow (RFC 8628).
- **Validator dashboards** — gate access to subnet validators; access auto-revokes when deregistered.
- **Token-gated content** — serve different content at different holder thresholds.
- **Subnet owner portals** — verify subnet ownership automatically, no allowlist required.

## Developer integration

1. Standard OAuth2/OIDC — no custom SDK.
2. JWKS endpoint for resource-server validation.
3. Token claims include `hotkey`, `coldkey`, `scope`, and `sub`.

## Trust & security

Bittensor Auth is a centralised layer on a decentralised system — and it is open source and self-hostable.

- **Hosted service** — configure an auth client with Taostats Pro.
- **Self-hosted** — run your own gateway.
- **Explore** — test flows at [auth.taostats.io](https://auth.taostats.io).

## Get started

[Configure an auth client](https://taostats.io/bittensor-auth) with Taostats Pro, or [view the project on GitHub](https://taostats.io/bittensor-auth) to self-host your own gateway.
