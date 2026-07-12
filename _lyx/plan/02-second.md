# 02 — second: write result2 and run the chain verify

## Intent

Chain end: create result2.md and run the chain's real verify, which requires batch 01's
result1.md to be present (the chain is only green as a whole).

## Scope

- result2.md

## Cards

### Card 02.1 — write result2

**What:** Create `result2.md` containing the single line `OK2`.
**Context:** none
**Edits:** none
**Creates:**
- `result2.md`
**Deletes:** none
**Moves:** none

## verify:

test -f result1.md
