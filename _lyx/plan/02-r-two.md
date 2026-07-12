# 02 — r-two: create r2.md

## Intent

Create `r2.md` at the repo root containing exactly the single line `OK`.

## Scope

- r2.md

## Cards

### Card 02.1 — create r2.md

**What:** Create `r2.md` at the repo root containing exactly the single
line `OK`. Commit it.
**Context:** none
**Edits:** none
**Creates:**
- `r2.md`
**Deletes:** none
**Moves:** none

## verify:

pwsh -NoProfile -Command "if ((Get-Content r2.md -Raw).Trim() -eq 'OK') { exit 0 } else { exit 1 }"
