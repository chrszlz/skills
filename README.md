# Skills

A small, reusable library of workflow skills for spec-first engineering. 🧭

This repo is meant to help a small team move faster without becoming casual about system design. The default motion is simple: write down the intended change, challenge whether it is the right change, refine the spec until it is implementation-ready, then build from that agreement.

## Core Workflow

```text
write-spec
  -> challenge-spec
  -> refine-spec
  -> implement-spec
  -> review-diff
  -> simplify-diff
```

For meaningful work, prefer two pull requests:

1. A docs-only spec PR where the team debates the problem, approach, risks, and verification plan.
2. An implementation PR that follows the accepted spec and updates it only when code reality reveals a real mismatch.

Small changes can combine these steps, but the thinking should still happen.

## Choosing the Route

Not every change needs a spec PR. Route by how much genuine approach or risk debate exists, not by line count:

- **Skip the spec** when an established in-repo pattern covers the change, it is reversible (no data migration or persisted state whose rollback would lose data), and it adds no new external contract (treat a persisted schema or on-disk format as external).
- **Combine into one lightweight PR** with a short embedded spec when the approach is clear but an assumption needs to be written down and checked.
- **Spec-first (two PRs)** when there is a real decision to debate, multiple systems or contracts are touched, or the change is hard to reverse.

Verify any "it is just like X" assumption before choosing to skip; if you cannot verify it, combine rather than skip. The `write-spec` skill carries the canonical rubric.

## Skill Index

| Skill | Use it when |
| --- | --- |
| `write-spec` | Turning an idea into an implementation-ready plan before coding. |
| `challenge-spec` | Reviewing a spec for necessity, system fit, risk, and simpler alternatives. |
| `refine-spec` | Incorporating feedback into a clearer, mergeable spec. |
| `implement-spec` | Building from an accepted or explicitly approved spec. |
| `review-diff` | Reviewing an implementation diff against behavior, tests, and the spec. |
| `simplify-diff` | Reducing unnecessary abstraction, one-offs, and surface area after code works. |

## Repository Shape

Each skill lives in a folder named after the skill:

```text
skill-name/
  SKILL.md
  agents/openai.yaml
```

Root-level docs explain the broader workflow. Per-skill folders should stay lean: no local README files, no extra references unless the skill truly needs progressive disclosure.

## Ethos

The point is not ceremony. The point is better judgment under pressure.

Good specs help answer:

- Is this the correct solve?
- Do we actually need this change?
- Is this an improvement, or does it feel like a hack?
- Are we using existing systems as intended?
- Does this duplicate a concept that already exists?

See the Challenge Stance in `docs/workflow-ethos.md` for the canonical question set.

The skills are intentionally generic. Keep project-specific rules in the project that owns them.

## Continuing This Work

This is an initial seed, not a finished doctrine. Use `docs/pressure-scenarios.md` to forward-test the skills on realistic tasks, then tighten the language where agents drift, overbuild, skip evidence, or fail to challenge a weak plan.
