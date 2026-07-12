---
format: 2
approved: true
---

# Plan: one slow batch, one quick batch

Batch 01 simulates a long-running migration (a mandatory 150-second wait)
before writing its marker file; batch 02 is a quick marker file.

## Batch Index

- 01 — slow (1 card) — run the 150s migration wait, then create w1.md containing OK
- 02 — quick (1 card) — create w2.md containing OK
