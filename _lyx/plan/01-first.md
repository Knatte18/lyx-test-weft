# 01 — first: create wr4a.md, verify always passes

## Intent

Create the marker file `wr4a.md` and commit it, then run a verify that always
succeeds.

## Cards

### Card 01.1 — create wr4a.md

**What:** Create `wr4a.md` at the repo root containing the single line `OK`,
and commit it.
**Context:** none
**Edits:** none
**Creates:**
- `wr4a.md`
**Deletes:** none
**Moves:** none

## Scope

- wr4a.md

## verify:

bash -c "test -f wr4a.md"
