# 01 — stuckv: create s1r5.md, verify always fails

## Intent

Create the marker file, then a verify command that always exits non-zero so
the batch cannot pass and must report stuck after exhausting self-fix.

## Cards

### Card 01.1 — create s1r5.md

**What:** Create `s1r5.md` at the repo root containing the single line `OK`,
and commit it. The batch's verify command will nonetheless always fail; that
is expected — do not try to make it pass by editing the verify.
**Context:** none
**Edits:** none
**Creates:**
- `s1r5.md`
**Deletes:** none
**Moves:** none

## Scope

- s1r5.md

## verify:

pwsh -NoProfile -Command "exit 1"
