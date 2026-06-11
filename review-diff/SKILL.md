---
name: review-diff
description: Use when reviewing an implementation diff for correctness, regressions, missing tests, boundary issues, or divergence from an accepted spec
---

# Review Diff

## Overview

Review an implementation diff for correctness first. Prioritize behavioral bugs, regressions, missing tests, boundary violations, and divergence from the accepted spec.

## Workflow

1. **Understand Intent**
   - Read the spec, issue, or stated goal.
   - Identify required behavior and non-goals.
   - Inspect the relevant diff and nearby code.

2. **Check Spec Compliance**
   - Does the diff build the agreed behavior?
   - Did it silently add, omit, or change scope?
   - Are docs, tests, and contracts aligned with the implementation?

3. **Look for Bugs**
   - Review data flow, state changes, error handling, permissions, concurrency, migrations, and cleanup.
   - Prefer concrete failure scenarios over broad style concerns.
   - Check that targeted tests cover the important behavior.

4. **Report Findings**
   - Findings first, ordered by severity.
   - Include file and line references when available.
   - Explain impact and a concrete fix direction.

## Output Format

Severity: P1 blocks merge; P2 should fix; P3 is an optional refinement.

```markdown
## Findings

- [P1] Short title
  File/line, impact, and suggested fix.

## Open Questions

- Only questions that affect correctness or approval.

## Test Gaps

- Missing or unrun verification that matters.
```

If there are no findings, say so clearly and name any residual risk or test gap.

## Common Mistakes

- Do not lead with summaries before findings.
- Do not bury correctness issues under style notes.
- Do not turn strategic disagreement into a code-review nit; send that back to the spec.
- Do not run a simplification pass unless requested or the review is complete.
