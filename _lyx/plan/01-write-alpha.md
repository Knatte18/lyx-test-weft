# 01 — write-alpha: create results/alpha.md

## Intent

Create `results/alpha.md` containing exactly the single line `OK-ALPHA`.
Stand-alone: after this batch the file exists and is committed.

## Scope

- results

## Cards

### Card 01.1 — write alpha marker

**What:** Create the file `results/alpha.md` whose entire content is the single
line `OK-ALPHA` (plus a trailing newline). Nothing else. Then commit it.
**Context:** none
**Edits:** none
**Creates:**
- `results/alpha.md`
**Deletes:** none
**Moves:** none
**Commit:** `01.1: add results/alpha.md marker`

## verify:

git cat-file -e HEAD:results/alpha.md
