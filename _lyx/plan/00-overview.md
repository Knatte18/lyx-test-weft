---
format: 5
approved: false
language: go
---

# Plan: Symmetric farewell path alongside the greeting

`services/api/main.go` exposes `ComposeGreeting`, which inlines its own empty-name check.
This plan factors that check into an unexported `defaultName`, adds a symmetric exported
`ComposeFarewell` that reuses it, covers the farewell with its own table-driven test, and
prints both lines from `main()`.

Exactly two files change — `services/api/main.go` and `services/api/main_test.go`. No new
file is created anywhere in the repo, no file gains an import, the package stays
`package main`, and `ComposeGreeting`'s name, signature, and output are frozen.

The three cards match the three commits the decision record prescribes, in that order. Each
one compiles and passes the suite standalone: card 1 is a behaviour-preserving refactor, card
2 lands an exported function that is briefly uncalled and untested (legal in Go, closed by
card 3), and card 3 adds the test and the wiring together.

## Card Index

1 — default-name-helper — extract the empty-name default into an unexported `defaultName` and have `ComposeGreeting` call it
2 — compose-farewell — add exported `ComposeFarewell`, mirroring `ComposeGreeting` and reusing the helper
3 — farewell-test-and-main-wiring — add table-driven `TestComposeFarewell` and print the farewell from `main()`

## Shared Decisions

- `defaultName` is unexported, lives in `services/api/main.go` above `ComposeGreeting`, and
  handles the empty string only: `"world"` when `name == ""`, `name` otherwise. Whitespace is
  not trimmed — that would be an unrequested behaviour change under cover of a refactor.
- Both composers call the helper inline inside `fmt.Sprintf`, so neither reassigns its
  parameter and the two read as structurally identical.
- `defaultName` gets no direct test; both composers' empty-name rows exercise it.
- Commit messages follow the branch convention `<step-number>: <kebab-slug>`, as in
  `1: format-greeting-helper` and `2: main-greeting-wiring`.
- The repo has no `go.mod`, a pre-existing property of the fixture that this plan does not
  fix (no new files). Tests therefore run in GOPATH mode from `services/api`.

## verify:

```
(cd services/api && GO111MODULE=off go test ./...)
gofmt -l services/api
```

`gofmt -l` must print nothing. Both commands are expected to hold at each of the three
commits, not only the last.
