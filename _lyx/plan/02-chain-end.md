# 02 — chain-end: create c2.md and run the chain's real verify

## Intent

Create `c2.md` at the repo root containing exactly the single line `OK`, then
run the chain's real verify, which checks both `c1.md` (from batch 01) and
`c2.md`.

## Scope

- c2.md

## Cards

### Card 02.1 — create c2.md

**What:** Create `c2.md` at the repo root containing exactly the single line
`OK`. Commit it.
**Context:** none
**Edits:** none
**Creates:**
- `c2.md`
**Deletes:** none
**Moves:** none

## verify:

pwsh -NoProfile -Command "if ((Get-Content c1.md -Raw).Trim() -eq 'OK' -and (Get-Content c2.md -Raw).Trim() -eq 'OK') { exit 0 } else { Write-Output 'chain files mismatch'; exit 1 }"
