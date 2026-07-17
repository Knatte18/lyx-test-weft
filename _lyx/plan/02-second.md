# 02 — second: create wr4b.md, verify always passes

## Intent

Create the marker file `wr4b.md` and commit it, then run a verify that always
succeeds.

## Cards

### Card 02.1 — create wr4b.md

**What:** Create `wr4b.md` at the repo root containing the single line `OK`,
and commit it.
**Context:** none
**Edits:** none
**Creates:**
- `wr4b.md`
**Deletes:** none
**Moves:** none

## Scope

- wr4b.md

## verify:

bash -c "test -f wr4b.md"
