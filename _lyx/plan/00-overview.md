---
format: 5
approved: true
language: go
---

# Plan: add FormatGreeting helper to services/api

Give `services/api` a `FormatGreeting` helper that formats a friendly greeting, falling back to the default name `"friend"` when the caller supplies an empty or whitespace-only name, and wire it into `main.go` so the package has a real consumer. Since no `go.mod` exists anywhere in the repo yet, one is added first so `go build ./...` and `go test ./...` can run.

## Card Index

1 — go-mod — add a root go.mod declaring module dummy-r2-greet
2 — format-greeting — add FormatGreeting with default-name fallback, wire it into main, and add a table-driven test

## verify:

```bash
go build ./...
go test ./...
```
