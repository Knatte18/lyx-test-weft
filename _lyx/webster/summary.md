# Add Farewell greeting helper and cross-reference it from Hello

Two-batch plan over `internal/greet`, executed sequentially per declared card dependency.

**Batch 01 — add-farewell** (`ecd3b2d105fb65c5a29ee547b86594b774d5d611`): added a `Farewell` greeting helper beside `Hello` in `internal/greet/greet.go`. Verified with `go build ./...`. No deviations reported.

**Batch 02 — hello-mentions-farewell** (`b8e0a46a98fefc833fc7b63132dc79135c4ed127`): extended `Hello`'s doc comment to point at the new `Farewell` helper as its closing counterpart. Verified with `go build ./...` (package has no test files). No deviations reported.

No plan-level `## verify:` section was present in `00-overview.md`, so no integration-suite stage ran. Both batches reported `status: done` with no self-fix retries or recoveries needed.
