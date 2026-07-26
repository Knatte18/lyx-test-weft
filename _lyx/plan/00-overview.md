---
format: 3
approved: true
---

# Plan: opus-r4 post-fix integration probe

Two trivial cards; card 2 breaks the plan-level `## verify:`. Confirms the
normal stuck-flow (Master reports stuck, webster bisect-escalates) is
unaffected by the OR4-1 fix.

## Card Index

1 — pgood — create pg-a.md
2 — pbad — create pg-bad.md (breaks the verify)

## verify:

test ! -f pg-bad.md
