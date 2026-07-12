---
format: 2
approved: true
---

# Plan: two-batch deferred-verify chain

Batch 01 is a deferred-verify intermediate; batch 02 is the chain end that
runs the real verify over both marker files.

## Batch Index

- 01 — chain-first (1 card) — create c1.md containing OK; verify deferred to batch 02
- 02 — chain-end (1 card) — create c2.md containing OK and run the chain's real verify
