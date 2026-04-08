---
title: "OEE Architecture"
description: "How the Open Execution Engine evaluates policy, issues attestations, and gates execution."
---

# Architecture

The Open Execution Engine (OEE) is Layer 1 of the Sigil stack. It is the domain-agnostic enforcement substrate. OEE does not know what industry you are deploying in or what your agent is trying to accomplish. It knows only what your policy permits, and it enforces that deterministically on every intent.

---

## Role in the Sigil Stack

```
Layer 3: Vertical Boilerplates (industry-specific configurations)
Layer 2: FAF (legal governance and fiduciary structure)
Layer 1: OEE (deterministic policy enforcement)    <-- this repo
```

---

## Core Responsibilities

1. Receive intent declarations from agent frameworks
2. Load and verify the operator's `warranty.md` policy at runtime
3. Evaluate intent against all four policy block types
4. Issue signed Intent Attestations for compliant intents
5. Manage consensus hold state (PENDING decisions, 24-hour TTL)
6. Expose the Sigil RPC and Bundler gateway endpoints

---

## Policy Evaluation Model

Policy evaluation is stateless per request and runtime-reloadable. The operator signs their `warranty.md` with an Ed25519 keypair. OEE verifies the signature at startup. If the policy has been modified after signing, OEE detects it and refuses to start.

Four typed policy blocks are evaluated in order:

| Block | Type | Behavior on violation |
|---|---|---|
| `## evm` | Hard limits on transaction value, chain, and action type | `DENIED` |
| `## tool_calls` | Blocked tools, blocked domains, blocked commands | `DENIED` |
| `## custom` | Operator-defined deny expressions | `DENIED` |
| `## soft_limits` | Daily aggregate caps (ETH value, tool call count) | `PENDING` |

---

## Authorization Decisions

OEE returns one of three decisions for every intent:

- **APPROVED**: intent is within policy. A signed Intent Attestation is issued immediately.
- **DENIED**: intent violates a hard policy rule. No attestation. Execution blocked.
- **PENDING**: intent exceeds a soft limit. A consensus hold is created with a 24-hour TTL. The agent cannot execute the held action until a human resolves the hold.

---

## Execution Gateways

OEE exposes guarded gateways for standard EOA and Account Abstraction flows:

- JSON-RPC: `POST /rpc/:chainId`
- ERC-4337 Bundler: `POST /bundler/:chainId`

Both gateways reject any write operation that does not present a valid, unexpired Intent Attestation.

---

## Vertical Boilerplates

Vertical boilerplates pre-assemble OEE + FAF for a specific deployment context. The first vertical is the Open Venture Engine (venture capital). Healthcare, banking, and enterprise verticals follow the same pattern.

Verticals live at `oee/verticals/<industry>/`.

---

## Contributing

OEE is a public repository. Contributions must follow the Sigil contribution guidelines. Do not include internal infrastructure details, IP addresses, secret names, or production topology in any file in this repository.
