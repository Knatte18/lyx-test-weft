# 01 — write-alpha: sleep long before writing results/delta.md

## Intent

Your VERY FIRST action must be running the single shell command `sleep 110`
as one blocking tool call and waiting for it to return — never backgrounded,
never split, never skipped, no other tool call before it. Only after it
returns create `results/delta.md` containing exactly the single line
`OK-DELTA` and commit it. The long blocking sleep is the point of this batch;
everything else is trivial.

## Scope

- results

## Cards

### Card 01.1 — sleep then write delta marker

**What:** As your first action run the single blocking shell command
`sleep 110` and wait for it to return. Only then create the file
`results/delta.md` whose entire content is the single line `OK-DELTA` (plus a
trailing newline), and commit it.
**Context:** none
**Edits:** none
**Creates:**
- `results/delta.md`
**Deletes:** none
**Moves:** none
**Commit:** `01.1: add results/delta.md marker`

## verify:

git cat-file -e HEAD:results/delta.md
