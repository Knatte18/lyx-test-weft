---
format: 2
approved: true
---

# Plan: chain restart test

A two-batch deferred-verify chain that writes two result files. Batch 01 is a
deferred-verify chain intermediate; batch 02 is the chain end that runs the real verify.

## Batch Index

- 01 — first (1 card) — write result1 as a deferred-verify chain intermediate
- 02 — second (1 card) — write result2 and run the chain verify
