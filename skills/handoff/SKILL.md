---
name: handoff
metadata:
  category: workflow
description: "Produce a compact, self-contained handoff block so a fresh chat can resume without the full transcript."
---

Produce a compact, self-contained handoff block so the next chat can resume from scratch without carrying this transcript.

Print the block exactly as shown. Fill every field except `next:`, which is optional: omit it or set "none" when no clear next action applies. Do not omit any other field.

```
goal:        <what we're ultimately trying to do, one line>
branch:      <git branch, or "none">
changed:     <comma-separated key files touched>
state:       <what works, what's half-done, what's untouched>
validation:  <last test/lint/build result, or "not yet run">
blockers:    <unresolved blockers, or "none">
decisions:   <choices made + why, so they aren't reversed; or "none">
reason:      <why handing off now: context limit, phase boundary, blocked, done>
next:        <exact next command or step; optional, omit or "none">
```

After printing the block, stop and tell me to continue from a fresh chat.

Note: a fresh chat has no memory of this one. This block is the whole handoff. Keep it dense and factual: real paths, real commands, no narrative. Verify claims before writing them (if a test passed, say so; if you assumed, don't assert).
