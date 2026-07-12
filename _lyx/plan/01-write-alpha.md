# 01 — write-alpha: sleep long before writing results/delta.md

## Intent

FIRST run the shell command `sleep 240` and wait the full 240 seconds for it
to finish — do not skip, shorten, or background it; if your tooling caps a
command at 2 minutes, run `sleep 110` three times back to back instead. Only
after sleeping create `results/delta.md` containing exactly the single line
`OK-DELTA` and commit it. The sleep is the point of this batch; everything
else is trivial.

## Scope

- results

## Cards

### Card 01.1 — sleep then write delta marker

**What:** Run `sleep 240` in the worktree and wait for it to complete (or
three consecutive `sleep 110` runs if a per-command timeout forces splitting).
Only after the full sleep has elapsed, create the file `results/delta.md`
whose entire content is the single line `OK-DELTA` (plus a trailing newline),
and commit it.
**Context:** none
**Edits:** none
**Creates:**
- `results/delta.md`
**Deletes:** none
**Moves:** none
**Commit:** `01.1: add results/delta.md marker`

## verify:

git cat-file -e HEAD:results/delta.md
