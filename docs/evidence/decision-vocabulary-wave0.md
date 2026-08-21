# Decision vocabulary Wave 0 evidence

Baseline: `origin/main` at `8903bb550706af2247a73337ade58b88478b0d1d`.

Method: a case-sensitive search over every Git text blob at the baseline found
one `APPROVED` occurrence and zero `ALLOWED` occurrences. The table accounts
for the complete baseline. Classifications use the closed set from the design.

| Baseline path | Occurrence | Classification | Action |
| --- | --- | --- | --- |
| `architecture.md` | `- **APPROVED**: intent is within policy. A signed Intent Attestation is issued immediately.` | gate-decision | The current documentation changes to the canonical ALLOWED literal. |

Totals at baseline: gate-decision 1; hold-status 0;
foreign-domain 0. The current allowlist identifies the one retained or
canonicalized occurrence by exact path, literal, trimmed line, and count.

## Execution-authority classification

This repository contains zero entry points that consume a Sigil decision
response and authorize execution from its status. It therefore receives no
decision-capability or import/architecture gate in this program.

Repository-specific surfaces were checked. OEE contains architecture and Warrant template documentation only; no executable engine or decision consumer is present.

A future decision-response consumer invalidates this zero-entry-point
classification and requires a new Phase 0 inventory before merge.

## Literal gate and forced-failure proof

The advisory command is
`python3 scripts/decision_literal_gate.py`. It scans declared text surfaces,
reports unknown occurrences, and exits zero in Wave 1. The same command with
`--blocking` fails closed. The planted proof at
`tests/decision_literal_gate_proof.py` demonstrates a clean blocking pass, a
planted blocking failure with path evidence, and an advisory report.

## Security-seam classification

Trigger map version 1.1 classifies this diff as security-seam because
`.github/workflows/decision-literal-gate.yml` matches
`.github/workflows/**`. The minimality ladder is off. The final exact-head
review must use the security-seam gate.

## Greptile update-review activation proof

This pull request includes an evidence-only follow-up commit after the v3
`triggerOnUpdates` setting became active. Merge remains blocked until Greptile
reviews that exact follow-up head. The hosted review receipt is recorded in the
central execution run log rather than copied into this source artifact.
