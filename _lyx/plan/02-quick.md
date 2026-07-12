# 02 — quick: create w2.md

## Intent

Create `w2.md` at the repo root containing exactly the single line `OK`.
Stand-alone: assumes batch 01 is committed.

## Scope

- w2.md

## Cards

### Card 02.1 — create w2.md

**What:** Create `w2.md` at the repo root containing exactly the single line
`OK`. Commit it.
**Context:** none
**Edits:** none
**Creates:**
- `w2.md`
**Deletes:** none
**Moves:** none

## verify:

pwsh -NoProfile -Command "if ((Get-Content w2.md -Raw).Trim() -eq 'OK') { exit 0 } else { Write-Output 'w2.md content mismatch'; exit 1 }"
