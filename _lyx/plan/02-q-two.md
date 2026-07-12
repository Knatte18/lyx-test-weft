# 02 — q-two: create q2.md

## Intent

Create `q2.md` at the repo root containing exactly the single line `OK`.

## Scope

- q2.md

## Cards

### Card 02.1 — create q2.md

**What:** Create `q2.md` at the repo root containing exactly the single
line `OK`. Commit it.
**Context:** none
**Edits:** none
**Creates:**
- `q2.md`
**Deletes:** none
**Moves:** none

## verify:

pwsh -NoProfile -Command "if ((Get-Content q2.md -Raw).Trim() -eq 'OK') { exit 0 } else { exit 1 }"
