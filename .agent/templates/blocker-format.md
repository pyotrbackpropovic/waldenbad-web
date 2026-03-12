# Blocker Entry Format

File: `.agent/blockers.md`

## Adding a blocker (agent)

```markdown
## BLOCKER-<number>: <Title>
**Status:** OPEN
**Raised:** YYYY-MM-DD
**Context:** What you were trying to do.
**What I tried:** Approaches attempted (be specific — include commands, errors, file paths).
**Question:** What you need from the operator to proceed.
```

## Operator response

The operator edits the file and adds:

```markdown
### Operator response (YYYY-MM-DD):
Answer to the question. As specific as possible.
```

## Agent acknowledgment

On next session, read the response and add:

```markdown
### Agent acknowledgment (YYYY-MM-DD):
Understood. <Brief note on how you will proceed.>
```

Then update `**Status:**` to `RESOLVED`.
