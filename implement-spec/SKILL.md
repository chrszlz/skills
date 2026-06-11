---
name: implement-spec
description: Use when implementing code from an accepted or explicitly approved spec, especially after a docs-only spec review
---

# Implement Spec

## Overview

Build from an accepted spec as a contract. Implementation should verify code reality, proceed in focused slices, and avoid silently changing strategy.

## Preconditions

- The spec is accepted, merged, or explicitly approved for implementation.
- The implementation scope is clear enough to start.
- Required local project instructions and domain skills have been read.

## Workflow

1. **Preflight the Spec**
   - Re-read the spec and identify required behavior, non-goals, and verification.
   - Inspect the current code enough to confirm the plan still fits.
   - Stop and report if the codebase contradicts the spec in a strategy-changing way.

2. **Slice the Work**
   - Implement the smallest coherent behavior first; build what the spec needs now, not hooks for futures it does not have.
   - Keep each slice reviewable.
   - Prefer existing patterns and owning abstractions.
   - Name new code to match the surrounding system's conventions, and prefer the clear name over the clever one.

3. **Verify Each Slice**
   - Run targeted tests or checks that prove the behavior: name the behavior and the check that would fail if it regressed. Target what is new or at risk, not checks that only re-verify unchanged behavior.
   - Add or update tests where the spec requires evidence.
   - Treat failures as information; do not widen scope casually.

4. **Track Spec Drift**
   - If implementation reveals a real mismatch, stop and get the spec change agreed before continuing; documenting a unilateral change and proceeding on your own approval is still drift.
   - Changing the approach without writing it down, even when the change feels small or obvious, is silent drift.
   - Do not quietly replace the agreed approach with a new one.

5. **Prepare for Review**
   - Summarize what changed relative to the spec.
   - Name tests run and any remaining gaps.
   - Hand off to review and simplification as separate passes.

## Stop Conditions

Stop and ask for direction when:

- The accepted spec is materially wrong.
- The implementation requires a different architecture than the spec chose.
- A required dependency, contract, or migration is missing.
- Verification cannot prove the promised behavior.

## Common Mistakes

- Treating the spec as inspiration instead of a contract.
- Implementing future follow-ups because the files are nearby.
- Skipping preflight and discovering mismatch late.
- Combining correctness review and simplification into a single rushed pass.
