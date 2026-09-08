# Card 2 — Hello mentions Farewell

**Edit:**
- `internal/greet#Hello`

**Uses:**
- `internal/greet#Farewell`

**Intent:**
Once `Farewell` exists, `Hello`'s own doc comment should point a reader at it, so the pair is
discoverable from either end. Extend `Hello`'s doc comment with a second sentence naming
`Farewell` as its closing counterpart. Do not change `Hello`'s body or its return value.

**ImpactSummary:** Doc-comment only — no caller of `Hello` observes any behavioural change.

**Verify:**
`go build ./...`
