# 01 — write-alpha: create results/gamma.md under an unfixable verify

## Intent

Create `results/gamma.md` containing exactly the single line `OK-GAMMA` and
commit it. The batch's verify: command below is intentionally impossible to
satisfy (the empty git tree contains no file, and no commit can ever change
that), so after the bounded self-fix attempts this batch MUST be reported
`status: stuck`, `tests: red`, with a stuck_reason naming the verify command
and what was attempted. Do not spend more than the allowed self-fix attempts.

## Scope

- results

## Cards

### Card 01.1 — write gamma marker

**What:** Create the file `results/gamma.md` whose entire content is the single
line `OK-GAMMA` (plus a trailing newline). Nothing else. Then commit it.
**Context:** none
**Edits:** none
**Creates:**
- `results/gamma.md`
**Deletes:** none
**Moves:** none
**Commit:** `01.1: add results/gamma.md marker`

## verify:

git cat-file -e 4b825dc642cb6eb9a060e54bf8d69288fbee4904:unfixable-verify-sentinel
