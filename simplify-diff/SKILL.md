---
name: simplify-diff
description: Use when a working diff needs a dedicated simplification pass to reduce abstraction, one-offs, compatibility paths, naming debt, or unnecessary surface area
---

# Simplify Diff

## Overview

Improve the final shape of working code without changing intended behavior. Simplification is a separate pass from correctness review.

## Preconditions

- The intended behavior is understood.
- The diff is working or close enough that simplification will not hide unresolved design questions.
- Relevant tests or checks are known.

## Workflow

1. **Freeze Behavior**
   - Identify what must remain true.
   - Use existing tests, specs, or manual checks as the behavior boundary.

2. **Inspect Shape**
   - Look for speculative abstractions, duplicated branches, one-off helpers, broad configuration, stale compatibility, names that fight local conventions or obscure intent, and unnecessary public surface area.
   - Check whether repeated local fixes reveal a missing shared system.

3. **Simplify**
   - Delete before abstracting.
   - Localize behavior before making it reusable.
   - Collapse layers that do not carry meaning.
   - Rename when names are hiding the simpler model.
   - Keep compatibility paths only when they have a clear owner, expiry, and deletion story.

4. **Verify**
   - Run targeted checks that prove behavior did not change: name the behavior and the check that would fail if it regressed.
   - Report any simplification that was intentionally deferred.

## Output Format

```markdown
## Simplifications

- What changed and why behavior is preserved.

## Deferred

- Simplifications not taken and why.

## Verification

- Commands or checks run.
```

## Common Mistakes

- Do not reopen product strategy unless the diff reveals the spec is wrong.
- Do not introduce a new abstraction just to make code look tidy.
- Do not remove compatibility behavior without evidence it is unused or explicitly out of scope.
- Do not claim simplification is safe without verification.
