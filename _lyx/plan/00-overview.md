---
format: 5
approved: true
language: go
---

# Plan: rename the default-name helper and follow it through the docs

`services/api/main.go` carries an unexported helper `defaultName` that both `ComposeGreeting`
and `ComposeFarewell` delegate their empty-name default to.
Its name reads as a noun where every call site uses it as an operator, so this plan retargets
the identifier to `orDefault`, notes the delegation in `ComposeFarewell`'s godoc, and records
the farewell path in the repository README.

## Card Index

1 — rename-default-helper — retarget the unexported helper's identifier to `orDefault`
2 — farewell-doc — note the shared default helper in `ComposeFarewell`'s godoc
3 — readme-note — record the farewell path in the repository README

## verify:

```
(cd services/api && GO111MODULE=off go test ./...)
```
