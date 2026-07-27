---
round: 1
target: C:\Code\lyx-test-HUB\lyx-test\r2-gate.txt
fixed: []
deferred:
  - id: F1
---

## Summary

Nothing was fixed this round.

## Fixed

None.

## Deferred (with reason)

- **F1** — [BLOCKING] artifact lacks a formal provenance header
  (`C:\Code\lyx-test-HUB\lyx-test\r2-gate.txt:1`). Deferred, not fixed, per an explicit
  operator-set constraint in this round's rubric: it directs that this exact finding be
  reported every round "regardless of what the file contains" and states it must "never" be
  marked fixed. That is a standing operator decision governing this round, not a capability gap
  on my part — attempting to remediate it (e.g. by adding any header to the file) would
  contradict the rubric's explicit instruction, so no edit was made to the target file this
  round.
