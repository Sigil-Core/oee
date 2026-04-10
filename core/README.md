# OEE Core

Shared primitives for all OEE verticals. Every vertical inherits from this layer.

The core layer provides:

- **Sigil Action Provider** — the direct integration point between any agent framework and sigil-sign. Handles intent submission, attestation receipt, and error routing.
- **`warranty.md` format reference** — the canonical policy format parsed by Sigil Lex at runtime.

Verticals do not reimplement these primitives. They configure them.

## Usage

Copy the Sigil Action Provider into your vertical's integration layer and point it at your deployment's `sigil-sign` endpoint. Configure your `warranty.md` using the format reference or [Sigil Warrant](https://sigilcore.com).

## Files

| File | Purpose |
|---|---|
| `sigil-action-provider.js` | Sigil Sign integration for agent frameworks |
| `warranty.example.md` | Canonical `warranty.md` format reference |
