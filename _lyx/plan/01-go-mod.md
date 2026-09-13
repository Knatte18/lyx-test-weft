# Card 1 — add go.mod

**Create:**
- `go.mod`

**Intent:** Declare a Go module at the repo root so `go build ./...` and `go test ./...` have a module to run against. Use module path `dummy-r2-greet` and the Go version available in the environment (1.26). No dependencies are needed — the package only uses the standard library.

**Commit:** 1: add go.mod for module dummy-r2-greet
