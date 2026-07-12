---
verify: deferred
chain-end: 2
---

# 01 — chain-first: create c1.md (deferred verify)

## Intent

Create `c1.md` at the repo root containing exactly the single line `OK`.
This is a deferred-verify chain intermediate: run NO verify command and
report `tests: skipped`. The chain's real verify runs in batch 02.

## Scope

- c1.md

## Cards

### Card 01.1 — create c1.md

**What:** Create `c1.md` at the repo root containing exactly the single line
`OK`. Commit it. Do not run any verify command (this batch's verify is
deferred to the chain end); report `tests: skipped`.
**Context:** none
**Edits:** none
**Creates:**
- `c1.md`
**Deletes:** none
**Moves:** none
