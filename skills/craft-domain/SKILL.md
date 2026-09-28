---
name: craft-domain
metadata:
  category: domain-design
description: "Create or evolve the project's DDD model in DOMAIN.md (Markdown + Mermaid), using grill-me to settle each change."
---

Own the project's domain model in `DOMAIN.md`. Only this skill writes it.

- Read `DOMAIN.md` if it exists; otherwise start from the skeleton below.
- Use `/grill-me` on the change I want until it's settled.
- Show the proposed edits, apply them only after I confirm.
- One term, one meaning. Unknowns go to Open questions, never invented.
- Every change adds a line to Decisions: date, what, why.

Skeleton:

````markdown
# Domain

## Glossary
| Term | Meaning | Context |

## Context map
```mermaid
flowchart LR
```

## <Context name>
```mermaid
classDiagram
```
Invariants:
- 

## Decisions
- YYYY-MM-DD: what, why

## Open questions
- 
````
