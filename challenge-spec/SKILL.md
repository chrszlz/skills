---
name: challenge-spec
description: Use when an existing plan or spec needs critical peer review for necessity, system fit, simpler alternatives, hidden assumptions, or implementation risk
---

# Challenge Spec

## Overview

Review a spec like a serious peer. Be constructive, evidence-seeking, and slightly adversarial in thought: protect the system from unnecessary work, hidden hacks, and weak plans.

## Stance

- Do not perform generic devil's advocacy.
- Challenge the strongest version of the proposal.
- Every finding must cite a concrete referent: a spec section, file, invariant, or failure scenario. A concern with no concrete referent is not a finding; drop it or turn it into a question.
- Look for simpler or more systemic alternatives.
- Separate must-fix issues from useful refinements.
- Preserve momentum when the plan is good enough. "Good enough" means no unaddressed P1 and no unowned systemic risk, not that the author is in a hurry.

## Workflow

1. **Necessity**
   - What problem is actually being solved?
   - Do users, operators, maintainers, or the product need this?
   - What happens if the team does nothing?

2. **System Fit**
   - Does this belong where the spec puts it?
   - Is there an existing abstraction, contract, workflow, or data model that should own it?
   - Does the plan create another one-off where a shared system should improve instead?
   - A Non-Goal that exists to dodge system fit (such as "not refactoring the duplicated concept") is itself a finding, not a boundary to accept.

3. **Correctness and Risk**
   - Which invariants must stay true?
   - What edge cases, migrations, concurrency issues, permissions, data integrity risks, or failure modes are missing?
   - What will be hard to roll back or delete later?

4. **Simplification**
   - What is the smallest durable version of the plan?
   - Can compatibility, configuration, abstraction, or branching be removed?
   - What should be explicitly deferred?
   - Simplify the plan here; code-shape simplification belongs to `simplify-diff` after the code works.

5. **Verification**
   - Does the test plan prove the important behavior?
   - Does verification target what is new or at risk, rather than re-verifying copied behavior?
   - Are docs, specs, tests, and external contracts kept in sync?
   - Is the implementation plan reviewable in focused slices?

## Output Format

Severity: P1 blocks acceptance; P2 should fix before implementation; P3 is an optional refinement. Default to P1 for data loss, security, external-contract breakage, or correctness gaps that make the spec unsafe to implement. Treat systemic risk as P1 only when it blocks ownership or correctness; otherwise make it P2 with a concrete resolution path.

Lead with findings, ordered by importance:

```markdown
## Findings

- [P1] Short title
  Concrete referent, why it matters, and suggested resolution.

## Questions

- Decision-blocking questions only.

## Suggested Spec Edits

- Concrete changes that would make the spec clearer or safer.

## Recommendation

Accept, accept with edits, or request changes.
```

## Challenge Questions

Use these when the spec feels too implementation-led:

- Is this the correct solve?
- Do we actually need this change?
- Is this an improvement, or does it feel like a hack?
- Are repeated one-offs telling us to improve the surrounding system?
- What would make future maintainers misunderstand this?
- What can be deleted if this lands?

## Common Mistakes

- Letting author urgency lower the bar. Urgency is not evidence; necessity is argued on the proposal's merits, not the author's deadline.
- Producing a generic risk list instead of findings tied to concrete referents.
- Performative devil's advocacy that does not change the plan.
- Nitpicking naming or style while missing a system-fit problem.
- Requesting changes without separating must-fix from nice-to-have.
- Downgrading a referenced finding into a gentle question to avoid blocking.
- Waving through a new one-off when the spec should consolidate an existing concept.
