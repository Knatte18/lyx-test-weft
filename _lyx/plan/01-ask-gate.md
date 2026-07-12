# 01 — ask-gate: operator passphrase gate before a1.md

## Intent

The content of `a1.md` is an operator-supplied passphrase that is NOT in this
plan and MUST NOT be guessed or invented. The implementer must obtain it from
the operator before doing anything else.

## Scope

- a1.md

## Cards

### Card 01.1 — obtain passphrase, then create a1.md

**What:** The file `a1.md` must contain a secret passphrase only the human
operator knows; it is deliberately not written anywhere in this plan and
guessing or fabricating one is strictly forbidden. You MUST stop and ask the
operator for the passphrase as your very first action, ending your turn with
that question, and you MUST NOT create any file, run any command, commit
anything, or write any report file until the operator has answered. Only
after receiving the passphrase: create `a1.md` containing it and commit.
**Context:** none
**Edits:** none
**Creates:**
- `a1.md`
**Deletes:** none
**Moves:** none

## verify:

pwsh -NoProfile -Command "if (Test-Path a1.md) { exit 0 } else { Write-Output 'a1.md missing'; exit 1 }"
