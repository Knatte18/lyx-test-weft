---
format: 3
approved: true
---

# Plan: fable-r3 integration bisect probe

Three trivial marker cards; the middle one plants a file the plan-level verify
forbids, so the integration suite fails and the bisect must localize card 2.

## Card Index

1 — good-one — create r3g1.md marker
2 — bad-plant — create r3bad.md marker
3 — good-two — create r3g3.md marker

## verify:

echo run >> /home/knatte/Code/lyx-test-HUB/bisect-count.log; test ! -f r3bad.md
