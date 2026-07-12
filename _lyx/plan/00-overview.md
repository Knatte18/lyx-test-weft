---
format: 2
approved: true
---

# Plan: sandbox builder suite P2 — guaranteed-stuck batch plus one trivial batch

Batch 01 attempts a trivial file write but carries a verify: command that can
never pass (it asks git whether the empty tree contains a file), so its
implementer must exhaust its self-fix attempts and report stuck. Batch 02 is
the trivial beta marker, kept for pause-boundary checks.

## Batch Index

- 01 — write-alpha (1 card) — create results/gamma.md, then fail an unfixable verify and report stuck
- 02 — write-beta (1 card) — create results/beta.md containing the single line OK-BETA
