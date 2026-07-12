# 01 — pause-one: create p1.md

## Intent

Create `p1.md` at the repo root containing exactly the single line `OK`.
Stand-alone: after this batch the file exists and is committed.

## Scope

- p1.md

## Cards

### Card 01.1 — create p1.md

**What:** Create `p1.md` at the repo root containing exactly the single line
`OK`. Commit it.
**Context:** none
**Edits:** none
**Creates:**
- `p1.md`
**Deletes:** none
**Moves:** none

## verify:

pwsh -NoProfile -Command "if ((Get-Content p1.md -Raw).Trim() -eq 'OK') { exit 0 } else { Write-Output 'p1.md content mismatch'; exit 1 }"
