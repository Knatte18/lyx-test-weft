---
format: 2
approved: true
---

# Plan: sandbox builder suite P1 — two trivial result files

Write two fixed-content marker files under `results/`, one per batch, so the
builder batch loop's mechanics (spawn, poll, weft commits, outcome) can be
observed with trivial implementer work.

## Batch Index

- 01 — write-alpha (1 card) — create results/alpha.md containing the single line OK-ALPHA
- 02 — write-beta (1 card) — create results/beta.md containing the single line OK-BETA
