---
format: 3
approved: true
---

# Plan: opus-r4 integration-bisect probe

Three trivial cards. Card 2 creates a file that makes the plan-level
integration `## verify:` command fail, so the integration fork reports FAILED
and webster's in-process SHA-bisect must localize card 2 as the offender.

## Card Index

1 — igood — create ig-a.md
2 — ibad — create ig-bad.md (breaks the verify)
3 — itail — create ig-c.md

## verify:

echo candidate >> /tmp/opusr4-bisect-count.log; test ! -f ig-bad.md
