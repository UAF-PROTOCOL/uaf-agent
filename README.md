# Universal Agent Firewall (UAF)

> Black box agents become glass box agents.

Live demo: [uaf-protocol.github.io/uaf-demo](https://uaf-protocol.github.io/uaf-agent)

---

## What is UAF?

UAF is a trust and safety layer that sits between an AI agent and the outside world.

Every time an agent tries to spend money, call an API, or share data, UAF intercepts it, checks it against rules the human set, and either allows or blocks it. Every decision is logged with a tamper-proof receipt.

---

## The Problem

AI agents act on your behalf, spending money, calling APIs, making deals. But there is no transparent way to scope what they can do, verify they did what you asked, or protect your data from leaking through their actions.

Right now every agent system has 4 unsolved problems:

- **Money** - no spend limits, no verified recipients, no proof of what was spent
- **Identity** - trust flows through centralized registries that can be revoked at any time
- **Promises** - no neutral enforcement layer, deals can be rewritten without consent
- **Privacy** - every API call leaks metadata about you: spending patterns, contacts, behavior

UAF solves all 4.

---

## How It Works

UAF intercepts every agent action before it executes and evaluates it against a policy the human defines:

- Is the spend amount within the limit?
- Is the recipient on the allowlist?
- Has the session expired?
- Would this action leak metadata?

If all checks pass, the action is approved and a tamper-proof receipt is generated. If any check fails, the action is blocked and the reason is logged.

---

## Features

**Spend policy enforcement**
Set a max spend per action, define allowlisted addresses, and set a session expiry window. The agent cannot go outside those bounds.

**Agent identity via ERC-8004**
UAF Agent is registered on Base Mainnet with a permanent on-chain identity. Not a username. Not an API key that can be revoked. A verifiable identity that nobody can take away.

**Tamper-proof receipts**
Every approved action generates a cryptographic proof hash with a timestamp. Immutable and verifiable by anyone.

**Metadata protection**
UAF intercepts outbound API calls before they leave. If your spending patterns or contacts would be exposed, the call is blocked.

---

## Live Demo

Try all 4 scenarios at [uaf-protocol.github.io/uaf-demo](https://uaf-protocol.github.io/uaf-demo)

| Scenario | What happens |
|---|---|
| Normal payment | Agent pays approved address within limit. Passes. Receipt generated. |
| Over limit | Agent tries to spend above policy limit. Blocked instantly. |
| Unknown recipient | Agent tries to pay an address not on the allowlist. Blocked. |
| Metadata leak | Agent makes an API call that exposes your data. Intercepted. |

No install. No signup. Open in browser and run.

---

## On-Chain Identity

UAF Agent is live on Base Mainnet, registered via ERC-8004.

- Agent ID: 35910
- Registry: [ERC-8004 Identity Registry on BaseScan](https://basescan.org/tx/0xaa35615f0e2e7ce824d8bb25794be986cb5e573b089311336352c5180174edc9)

---

## Tech Stack

- Vanilla HTML and JavaScript, zero dependencies, no build step
- ERC-8004 agent identity on Base Mainnet
- Runs entirely in the browser

---

## Roadmap

- [x] Policy engine with spend limits, allowlists, and session expiry
- [x] Metadata interception layer
- [x] Off-chain tamper-proof receipts
- [x] ERC-8004 on-chain agent identity
- [ ] On-chain receipt anchoring on Base
- [ ] npm SDK for agent integration
- [ ] Protocol-level trust registry for agent-to-agent verification

---

## Hackathon

Built for [The Synthesis](https://synthesis.md) hackathon.

Entered tracks: Agents With Receipts (ERC-8004), Agent Services on Base, stETH Agent Treasury, Let the Agent Cook.

---

## Follow the Build

Twitter/X: [@james_base_eth](https://x.com/james_base_eth)
GitHub: [github.com/UAF-PROTOCOL/uaf-agent](https://github.com/UAF-PROTOCOL/uaf-agent)
