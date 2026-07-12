# 02 — pause-two: create p2.md

## Intent

Create `p2.md` at the repo root containing exactly the single line `OK`.
Stand-alone: assumes batch 01 is committed.

## Scope

- p2.md

## Cards

### Card 02.1 — create p2.md

**What:** Create `p2.md` at the repo root containing exactly the single line
`OK`. Commit it.
**Context:** none
**Edits:** none
**Creates:**
- `p2.md`
**Deletes:** none
**Moves:** none

## verify:

pwsh -NoProfile -Command "if ((Get-Content p2.md -Raw).Trim() -eq 'OK') { exit 0 } else { Write-Output 'p2.md content mismatch'; exit 1 }"
