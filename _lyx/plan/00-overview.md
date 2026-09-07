---
format: 5
approved: true
language: go
---

# Plan: rename FormatGreeting to ComposeGreeting

`services/api` exports one greeting helper under a name that describes the wrong
job: `FormatGreeting` composes the whole greeting sentence rather than
formatting a pre-existing one. This plan renames it to `ComposeGreeting` and
follows the name through every reference the repository carries — the
declaration and its doc comment, the call inside `main()`, the call under test,
the helper's name embedded in the test's failure-message format string, and the
test function's own name.

Nothing else changes. The signature, the parameter name, the return type, the
body, and the empty-name default to `"world"` are preserved bit for bit, and no
symbol is added: no alias, no deprecated shim, no wrapper kept under the old
name. The repository is a fixture host for the weft sandbox, so its file
inventory is load-bearing for other tooling — `services/api/main.go` and
`services/api/main_test.go` are the only two files this plan touches, and no
file is added, moved, or deleted.

## Card Index

1 — compose-greeting-rename — Rename the helper and the test that exercises it, retargeting every reference the old name carries

## Shared Decisions

- **The old name is deleted outright.** The helper's in-repo callers are small
  and fully enumerable and nothing outside the repository can import it — the
  package is `package main` in a tree with no module path. A retained forwarder
  would defeat the point of the rename and add a symbol the task forbids.
- **No `sed`, and no repo-wide substitution.** The operator's standing
  instruction bans `sed`, and the identifier is retargeted occurrence by
  occurrence with the editing tools. Touching only the lines that carry the
  identifier keeps the diff minimal, keeps blame legible, and rules out
  collateral hits: `services/api/s2-note.txt`, `README.md`, and the driver state
  under `_lyx/` and `.lyx/` must all stay byte-identical.
- **The doc comment's leading word is retargeted; the rest stays verbatim.** Go
  requires a doc comment to begin with the declared name, so the first word must
  change. The description after it is still accurate.
- **No build scaffolding enters the tree.** No `go.mod` is defined anywhere in
  this repository and none may be introduced, so `go test` cannot run in place.
  The plan-level check below copies the two Go files to a throwaway directory
  outside the worktree and runs the suite there, leaving no scratch artifact
  behind inside the repository.

## Rename mechanic

1. Run `git mv <old> <new>` FIRST, before any other change to the moved file.
2. Then make ONLY surgical edits (package declaration, imports, identifier
   retargeting) — no unrelated rewrites.
3. A genuinely new file with no predecessor belongs in a separate `Create` card, never folded
   into the `Rename` pair.
4. Never write the relocated file from scratch and delete the original — that loses
   git history exactly as an unstructured create+delete pair would.

## verify:

```sh
test -z "$(gofmt -l services/api)"
! grep -rn FormatGreeting services/api
test "$(grep -c ComposeGreeting services/api/main.go)" = 3
test "$(grep -c ComposeGreeting services/api/main_test.go)" = 3
D="$(mktemp -d)" && cp services/api/main.go services/api/main_test.go "$D"/ && printf 'module scratch\n\ngo 1.26\n' > "$D"/go.mod && go -C "$D" test -v ./...
test -z "$(git status --porcelain)"
```
