# 01 — r-one: create r1.md

## Intent

Create `r1.md` at the repo root containing exactly the single line `OK`.

## Scope

- r1.md

## Cards

### Card 01.1 — create r1.md

**What:** Create `r1.md` at the repo root containing exactly the single
line `OK`. Commit it.
**Context:** none
**Edits:** none
**Creates:**
- `r1.md`
**Deletes:** none
**Moves:** none

## verify:

pwsh -NoProfile -Command "if ((Get-Content r1.md -Raw).Trim() -eq 'OK') { exit 0 } else { exit 1 }"
