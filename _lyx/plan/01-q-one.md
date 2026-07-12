# 01 — q-one: create q1.md

## Intent

Create `q1.md` at the repo root containing exactly the single line `OK`.

## Scope

- q1.md

## Cards

### Card 01.1 — create q1.md

**What:** Create `q1.md` at the repo root containing exactly the single
line `OK`. Commit it.
**Context:** none
**Edits:** none
**Creates:**
- `q1.md`
**Deletes:** none
**Moves:** none

## verify:

pwsh -NoProfile -Command "if ((Get-Content q1.md -Raw).Trim() -eq 'OK') { exit 0 } else { exit 1 }"
