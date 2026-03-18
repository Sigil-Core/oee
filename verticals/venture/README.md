# Open Venture Engine (OVE)

*The first OEE vertical — pre-configured for autonomous venture capital and fund deployment.*

![Status](https://img.shields.io/badge/status-active--development-black)
![Vertical](https://img.shields.io/badge/vertical-Venture--Capital-blue)
![Enforcement](https://img.shields.io/badge/enforcement-OEE-green)

---

## What OVE Is

OVE is the Open Execution Engine pre-wired for autonomous capital deployment. It gives founders, GPs, and DAOs the infrastructure to deploy AI agents as autonomous VCs — with full deterministic governance enforced before any capital moves.

OVE does not replace the OEE enforcement layer. It configures it for the venture capital domain: spend limits, action allowlists, chain permissions, and consensus gates tuned for fund mandates and fiduciary obligations.

**OVE is one vertical of OEE.** The enforcement architecture — Sigil Sign, Sigil Lex, Intent Attestations — is shared with every other vertical. OVE's contribution is the domain-specific configuration and boilerplate on top.

---

## The Problem OVE Solves

AI agents are increasingly capable of evaluating market conditions, identifying yield opportunities, and allocating capital. But handing an agent direct execution authority over a treasury introduces catastrophic risk.

Without structural guardrails, a rogue or hallucinating agent could:

- drain its own treasury
- execute unauthorized investments
- violate fiduciary mandates
- exceed fund governance constraints

OVE solves this by enforcing deterministic authorization **before execution**, not after capital moves.

---

## Architecture

OVE separates the agent's decision-making from its execution authority.

```
┌─────────────────────────┐
│     AI Agent (Brain)    │
│  ElizaOS / AgentKit /   │
│  LangChain / Custom     │
└────────────┬────────────┘
             │ Intent
             ▼
┌─────────────────────────┐
│      Sigil Sign         │  ← OEE Core enforcement layer
│  Sigil Lex evaluates    │
│  ASSURANCE.md policy    │
└────────────┬────────────┘
             │ Intent Attestation (Ed25519 JWT)
             ▼
┌─────────────────────────┐
│   Execution Engine      │
│  AgentKit / ERC-4337    │
│  RPC / Bundler Gateway  │
└─────────────────────────┘
```

The Brain proposes. Sigil authorizes. The Engine executes — only after attestation.

---

## Policy Configuration

OVE ships with a venture capital-tuned `ASSURANCE.md` template. Copy it to `config/ASSURANCE.md` and customize for your fund mandate.

Key Class 1 defaults:
- `max_transaction_eth: 31.25` (~$100,000 at 3,200 USD/ETH)
- `allowed_actions: wallet.transfer, contract.call`
- `allowed_chains: 1, 8453, 42161`

Key Class 3 default:
- `consensus_threshold_eth: 23.4` (~$75,000) — triggers a human approval hold

These are starting points. Your fund's legal mandate should drive the final values. Use the [ASSURANCE.md Drafter](https://sigilcore.com) to generate and sign your policy.

---

## Structure

```
verticals/venture/
├── README.md                   ← This file
├── ASSURANCE.md                ← VC-tuned policy template
├── agent/                      ← Agent orchestration logic
├── contracts/                  ← ERC-6551, Safe, Superfluid templates
├── integrations/               ← AgentKit and ElizaOS adapters
└── examples/                   ← End-to-end agent examples
```

---

## Getting Started

```bash
# Clone the OEE repo
git clone https://github.com/Sigil-Core/oee.git
cd oee/verticals/venture

# Copy and configure your policy
cp ASSURANCE.md config/ASSURANCE.md
# Edit config/ASSURANCE.md for your fund mandate
# Sign it at sigilcore.com before deploying

# Install dependencies
npm install

# Start your agent
npm run start
```

---

## Who OVE Is For

- Autonomous venture capital funds
- DAO treasury automation
- On-chain investment protocols
- Agentic yield strategies
- Founders deploying autonomous financial agents

---

## Legal Wrapper

OVE is designed to pair with the [Fiduciary Agent Framework (FAF)](https://github.com/Sigil-Core/faf) — the legal-technical bridge that wraps your OVE deployment in an LLC or DAO LLC structure to bound fiduciary liability.

OEE enforcement closes the execution gap. FAF closes the legal gap.

---

## Related

- [OEE Core](../../core/) — shared enforcement primitives
- [OEE Root](../../README.md) — framework overview
- [All Verticals](../) — other OEE verticals
- [Sigil Sign](https://github.com/Sigil-Core/sigil-sign) — execution firewall
- [FAF](https://github.com/Sigil-Core/faf) — legal wrapper
- [docs.sigilcore.com](https://docs.sigilcore.com) — full documentation
