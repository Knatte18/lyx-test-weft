# Card 1 — Add Farewell

**Create:**
- `internal/greet#Farewell`

**Intent:**
`internal/greet` has a `Hello` greeting and no closing counterpart, so a caller that wants to end a
conversation has to hand-write the string. Add a `Farewell` function beside `Hello`, in the same
file, returning the literal `"goodbye"`, with a one-line doc comment in the same style `Hello`
already uses.

**Verify:**
`go build ./...`
