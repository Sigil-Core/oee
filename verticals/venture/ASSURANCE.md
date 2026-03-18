# ASSURANCE Policy — Open Venture Engine (OVE)
<!-- Sigil Lex — Venture Capital Deployment Template -->
<!--
  Pre-tuned for autonomous VC and fund deployment.

  Copy to config/ASSURANCE.md and customise for your fund mandate.
  config/ASSURANCE.md is gitignored — never commit the live policy file.

  Limits below use 1 ETH = $3,200 USD as the conversion baseline.
  Adjust to your fund's actual mandate and current ETH price before deploying.

  Sign this file using the Sigil ASSURANCE.md Drafter at sigilcore.com before deploying.
-->

version: 1.0.0

## Class 1: Hard Rules
max_transaction_eth: 31.25
allowed_actions: wallet.transfer, contract.call
allowed_chains: 1, 8453, 42161
chain_actions:
  "1": wallet.transfer, contract.call
  "8453": wallet.transfer
  "42161": wallet.transfer

## Class 2: Soft Rules
daily_limit_eth: 156.25

## Class 3: Consensus Rules
consensus_threshold_eth: 23.4
consensus_require_hold: true
