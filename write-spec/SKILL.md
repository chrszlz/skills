---
name: write-spec
description: Use when deciding whether a change needs a spec, lightweight plan, or direct implementation, or when drafting an implementation-ready spec before code
---

# Write Spec

## Overview

Decide how much planning a change deserves, then write a durable spec when needed. Do the hard thinking before code starts: current reality, system fit, options, chosen approach, risks, and verification.

## When to Spec-First

Specs serve judgment, not ceremony. Route the change by how much genuine approach or risk debate exists, not by line count:

- **Skip the spec** when an established in-repo pattern already covers the change, the change is reversible, and it adds no new external contract. Treat persisted schemas, on-disk formats, cross-team APIs, and serialized surfaces as external contracts. Make the change directly and name the pattern you mirrored.
- **Combine into one lightweight pass** when the approach is clear but an assumption needs to be written down and checked. Ship one PR with a short embedded spec: problem, the assumption relied on, scope boundary, verification.
- **Full spec-first (two PRs)** when there is a real approach or risk decision to debate, the change touches multiple systems or contracts, or it is hard to reverse.

Verify any "it is just like X" analogy before choosing to skip. If you cannot verify it, combine and check it in the PR. When unsure, spec.

## Rules

- Do not implement while writing the spec. Spike only in a throwaway branch and bring findings back as evidence.
- Ground current-behavior claims in code, docs, tests, APIs, schemas, or product behavior. Mark claims as verified-from-source or as assumptions; cite the source for verified claims.
- Ask only questions that materially change approach, scope, or verification. Otherwise make a default assumption and record it.
- Treat the spec as a future review artifact, not a private note.
- Prefer the smallest durable system improvement over another local one-off.

## Workflow

1. **Orient**
   - Restate the requested outcome.
   - Identify affected systems, owners, contracts, and docs.
   - Read enough source material to describe the current behavior accurately.

2. **Test Necessity**
   - Ask whether the change should exist, and what happens if the team does nothing.
   - Enumerate existing implementations of the concept. If two or more similar implementations already exist, include consolidation as an option and reject it only with a concrete reason.
   - Name whether this is net-new behavior, replacement, migration, cleanup, or compatibility work.

3. **Compare Approaches**
   - Present 2-3 plausible approaches when the path is not obvious. If one is clearly correct, briefly name why alternatives were rejected.
   - Include tradeoffs, deletion opportunities, and failure modes.
   - Recommend one approach and explain why it best fits the system.

4. **Write the Spec**
   - Make decisions explicit and record them in the Decision Record.
   - Include non-goals and a focused implementation plan.
   - Include targeted verification: name the behavior, the check that would fail if it regressed, and prefer the narrowest useful check.

## Spec Shape

Use this structure unless the repo has a stronger local template:

```markdown
# Title

## Summary

## Current Reality

## Goals

## Non-Goals

## Options Considered

## Chosen Approach

## Implementation Plan

## Test and Verification Plan

## Risks and Open Questions

## Decision Record
```

Keep the Decision Record as a running log of resolved choices and rejected alternatives, so challenge and refinement do not lose history.

## Quality Bar

A good spec lets another engineer or agent implement without re-deciding strategy. Before finishing, confirm each; if any answer is "no" or "unclear", fix the spec rather than ship it:

- Is this the correct solve?
- Do we need this change?
- Is it an improvement rather than a hack?
- Where does this belong in the existing system?
- What is the smallest version that still works?
- What proves the implementation is correct?

## Common Mistakes

- Starting from the requested implementation instead of the underlying problem.
- Presenting invented or assumed behavior as verified current reality.
- Writing a spec that does not describe current behavior.
- Hiding uncertainty instead of naming open questions.
- Listing generic risks without tying them to the system.
- Skipping non-goals, which makes scope creep look like ambiguity.
