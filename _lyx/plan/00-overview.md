---
format: 5
approved: true
language: go
---

Fixture plan for crucible round 5's hub-mode crash-kill scenario: two small, independently
compilable cards over `internal/greet`, the second depending on the first, so the run produces two
sequential batches and a `kill -9` between them has something real to interrupt.

## Card Index

1 — add-farewell — add a Farewell greeting helper beside Hello
2 — hello-mentions-farewell — make Hello's doc comment point at the new Farewell helper
