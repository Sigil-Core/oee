# Contributing a Vertical to OEE

The Open Execution Engine is designed to grow. The venture capital vertical (Open Venture Engine) is the first. We welcome contributions that bring OEE's enforcement framework to new domains.

## What is a Vertical?

A vertical is a pre-configured OEE implementation for a specific deployment context. It provides:

1. A domain-tuned `warranty.md` policy template
2. Integration examples for relevant agent frameworks
3. Domain-specific documentation (legal context, compliance considerations, example use cases)
4. A `README.md` that explains who the vertical is for and how to use it

Vertical directories are named by domain (e.g. `venture`, `healthcare`, `banking`). Each vertical has a full product name and acronym documented in its `README.md`.

Verticals live in `/verticals/<domain>/` within this monorepo.

## Planned Verticals

| Domain Directory | Product Name | Status |
|---|---|---|
| `verticals/venture/` | Open Venture Engine (OVE) | ✅ Active |
| `verticals/healthcare/` | Open Healthcare Engine (OHE) | 🔜 Planned |
| `verticals/banking/` | Open Banking Engine (OBE) | 🔜 Planned |
| `verticals/enterprise/` | Open Enterprise Engine | 🔜 Planned |

## How to Contribute a New Vertical

1. Fork this repository
2. Create `/verticals/<domain-name>/` using a clear, lowercase domain word
3. Include at minimum:
   - `README.md` — what this vertical is for, who it serves, how to use it. Include the full product name and acronym here.
   - `warranty.md` — a domain-tuned policy template using the canonical Sigil Lex format (see `/core/warranty.example.md`)
4. Open a pull request with a description of the domain, the enforcement considerations specific to it, and any relevant compliance or regulatory context
5. Reference `/core/` primitives rather than reimplementing Sigil Sign integration

## Standards

All verticals must:

- Use the canonical `warranty.md` format defined in `/core/warranty.example.md`
- Route execution through Sigil Sign — no direct execution without attestation
- Document Class 1, 2, and 3 policy decisions and why they were set for the domain
- Not hardcode private keys, API credentials, or wallet addresses

## Questions

Open an issue or visit [docs.sigilcore.com](https://docs.sigilcore.com).
