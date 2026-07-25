---
format: 3
approved: true
---

# Plan: webster opus-r2 integration bisect

Three marker cards; card 2 creates a file the plan-level verify treats as a
failure, so the integration suite fails and the in-process bisect must localize
card 2.

## Card Index

1 — good-one — create wr2i-g1.md marker
2 — offending — create wr2i-offending.md marker
3 — good-two — create wr2i-g2.md marker

## verify:

test ! -f wr2i-offending.md
