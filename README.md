# Open Execution Engine (OEE)

*A deterministic enforcement monorepo for autonomous AI agents operating across multiple deployment domains.*

![Status](https://img.shields.io/badge/status-active--development-black)
![License](https://img.shields.io/badge/license-MIT-blue)
![Security](https://img.shields.io/badge/security-Intent--Attestation-green)

---

## What OEE Is

The **Open Execution Engine (OEE)** is an open-source monorepo that provides domain-specific implementations of the [Sigil Open Framework](https://github.com/Sigil-Core/sigil-open-framework) enforcement architecture.

OEE is organized into **verticals** — pre-configured enforcement stacks for specific deployment domains. Each vertical inherits shared enforcement primitives from `/core/` and adds domain-tuned policy templates, integration examples, and documentation.

The first vertical is **OVE (Open Venture Engine)** — a fully autonomous venture capital stack secured by deterministic Intent Attestation enforcement.

---

## Enforcement Architecture

Every OEE vertical uses the same enforcement layer:

```
┌─────────────────────────┐
│     AI Agent (Brain)    │
│  ElizaOS / AgentKit /   │
│  LangChain / Custom     │
└────────────┬────────────┘
             │ Intent
             ▼
┌─────────────────────────┐
│      Sigil Sign         │  ← Deterministic execution firewall
│  Sigil Lex evaluates    │
│   warranty.md policy    │
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

No transaction may execute on-chain without a valid Intent Attestation.

---

## Repository Structure

```
oee/
├── core/                  ← Shared enforcement primitives
│   ├── README.md
│   ├── sigil-action-provider.js
│   └── warranty.example.md
├── verticals/             ← Domain-specific implementations
│   ├── README.md
│   └── venture/           ← Open Venture Engine (OVE)
│       ├── README.md
│       ├── warranty.md
│       ├── agent/
│       ├── contracts/
│       ├── integrations/
│       └── examples/
└── CONTRIBUTING.md        ← Vertical contribution guide
```

---

## Verticals

| Directory | Product Name | Status |
|---|---|---|
| [`verticals/venture/`](./verticals/venture/) | Open Venture Engine (OVE) | ✅ Active |
| `verticals/healthcare/` | Open Healthcare Engine (OHE) | 🔜 Planned |
| `verticals/banking/` | Open Banking Engine (OBE) | 🔜 Planned |
| `verticals/enterprise/` | Open Enterprise Engine | 🔜 Planned |

---

# Getting Started

OEE is a monorepo. Choose your path:

### Deploy a vertical (recommended for most users)

Verticals are pre-configured OEE implementations for specific domains. Start with the vertical closest to your use case.

```bash
git clone https://github.com/Sigil-Core/oee.git

# Venture capital / fund deployment (Open Venture Engine)
cd oee/verticals/venture

# Follow the vertical's README for setup instructions
```

**Available verticals:** [→ Browse verticals](./verticals/)

### Build on OEE core (for framework contributors)

```bash
git clone https://github.com/Sigil-Core/oee.git
cd oee/core
# See core/README.md
```

### Contribute a new vertical

See [CONTRIBUTING.md](./CONTRIBUTING.md) for the vertical contribution guide.

---

## Related Repositories

- [Sigil Open Framework](https://github.com/Sigil-Core/sigil-open-framework) — open-source standard and doctrine
- [FAF](https://github.com/Sigil-Core/faf) — Fiduciary Agent Framework (legal wrapper)
- [sigil-attestations](https://github.com/Sigil-Core/sigil-attestations) — canonical Intent Attestation specification

---

## Documentation

Full documentation at [docs.sigilcore.com](https://docs.sigilcore.com)
