---
name: refine-spec
description: Use when review comments, open questions, or implementation discoveries need to be folded into a clearer mergeable spec
---

# Refine Spec

## Overview

Turn review feedback and open questions into a cleaner spec. Preserve useful disagreement as decisions, then leave the document ready for approval or implementation.

## Inputs

- The current spec.
- Review comments, requested changes, or unresolved questions.
- Any new evidence from code, docs, tests, product discussion, or prototypes.

## Workflow

1. **Collect Feedback**
   - Group comments by decision area.
   - Separate blockers, clarifications, polish, and follow-up ideas.
   - Identify contradictions between comments.

2. **Resolve Decisions**
   - Convert ambiguity into explicit choices.
   - When comments contradict and no owner is available to break the tie, make the call that best fits the system, record the tradeoff and the rejected side in the spec's Decision Record, and flag it for the owner; do not silently pick a side.
   - Record rejected approaches when they matter for future readers.
   - Keep non-goals visible.

3. **Rewrite for Implementation**
   - Tighten the summary and chosen approach.
   - Make implementation slices ordered and reviewable.
   - Align test plans with the behavior that matters.
   - Remove stale alternatives or mark them as rejected.

4. **Check Merge Readiness**
   - No unresolved blocker is hidden in prose.
   - The spec distinguishes required work from follow-up work.
   - Another engineer or agent can implement without re-deciding strategy.

## Output Modes

When editing the spec directly, include a short change summary. When only reviewing, produce:

```markdown
## Resolved Decisions

## Remaining Open Questions

## Suggested Spec Edits

## Merge Readiness
```

## Common Mistakes

- Treating every review comment as equally important.
- Accepting contradictory feedback without naming the tradeoff.
- Expanding scope while resolving comments.
- Removing decision history that future reviewers will need.
- Leaving "maybe" language in implementation-critical sections.
