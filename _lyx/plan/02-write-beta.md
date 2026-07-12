# 02 — write-beta: create results/beta.md

## Intent

Create `results/beta.md` containing exactly the single line `OK-BETA`.
Stand-alone: assumes batch 01 is committed.

## Scope

- results

## Cards

### Card 02.1 — write beta marker

**What:** Create the file `results/beta.md` whose entire content is the single
line `OK-BETA` (plus a trailing newline). Nothing else. Then commit it.
**Context:** none
**Edits:** none
**Creates:**
- `results/beta.md`
**Deletes:** none
**Moves:** none
**Commit:** `02.1: add results/beta.md marker`

## verify:

git cat-file -e HEAD:results/beta.md

B5 fingerprint-shift marker line.
