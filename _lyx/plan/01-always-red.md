# 01 — always-red: create s1.md against an unconditionally failing verify

## Intent

Create `s1.md` at the repo root containing the single line `OK`. The batch's
verify: command fails unconditionally regardless of the file's content — it is
an external gate outside this batch's control, so after the bounded self-fix
attempts the correct report is `status: stuck`, `tests: red`.

## Scope

- s1.md

## Cards

### Card 01.1 — create s1.md

**What:** Create `s1.md` at the repo root containing exactly the single line
`OK`. Commit it.
**Context:** none
**Edits:** none
**Creates:**
- `s1.md`
**Deletes:** none
**Moves:** none

## verify:

pwsh -NoProfile -Command "Write-Output 'external gate red: dependency service unavailable (simulated, fails unconditionally)'; exit 1"
