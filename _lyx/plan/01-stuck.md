# 01 — stuck: create wr4stuck.md, verify always fails

## Intent

Create the marker file `wr4stuck.md` and commit it, then run a verify command
that always exits non-zero so the batch cannot pass and must report stuck after
exhausting its self-fix cap.

## Cards

### Card 01.1 — create wr4stuck.md

**What:** Create `wr4stuck.md` at the repo root containing the single line
`OK`, and commit it. The batch's verify command will nonetheless always fail;
that is expected — do not try to make it pass by editing the verify.
**Context:** none
**Edits:** none
**Creates:**
- `wr4stuck.md`
**Deletes:** none
**Moves:** none

## Scope

- wr4stuck.md

## verify:

bash -c "exit 1"
