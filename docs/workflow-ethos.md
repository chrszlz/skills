# Workflow Ethos

This repo grew from a simple observation: a small team with broad domain ownership can move quickly, but only if the thinking scales with the codebase.

The target environment is a large but understandable product, owned by a very small number of engineers. That makes judgment more valuable than process volume. The workflow should help people and agents make better calls without making the team slower or more ceremonial.

## What We Are Optimizing For

- Better decisions before implementation.
- Fewer one-off fixes that quietly become permanent architecture.
- A clearer distinction between product need, system fit, and implementation convenience.
- More useful review conversations.
- Implementation PRs that are easier to review because the strategy was already debated.
- Simplification as a first-class step after the code works.

## The Spec-First Default

For meaningful work, prefer a docs-only spec PR before implementation. Use the spec PR to discuss the problem, the current system, options, chosen approach, risks, and verification plan.

After the spec is accepted, use a separate implementation PR. The implementation can update the spec if code reality reveals an important mismatch, but it should not silently drift from the accepted plan.

This split is not meant to slow down small changes. It is meant to keep big decisions from being hidden inside code review.

## The Challenge Stance

The best challenge is not performative devil's advocacy. It is a serious peer asking whether the proposal deserves to exist in the system.

Useful questions include:

- Is this the correct solve?
- Do we actually need this change?
- Is this an improvement, or does it feel like a hack?
- Are we using existing systems as intended?
- Does this duplicate a concept that already exists?
- Are repeated one-offs telling us to improve the surrounding system?
- What is the smallest durable version of this idea?
- What should be deleted or simplified if this lands?

## The Delivery Stance

Implementation should feel comparatively boring after a good spec. Build in focused slices, verify the behavior that matters, review against the spec, then run a separate simplification pass.

Review should find correctness and risk issues. Simplification should improve the final shape: fewer abstractions, better names, smaller surface area, and less accidental compatibility.

## What To Avoid

- Specs that merely restate the requested implementation.
- Challenge passes that only list generic risks.
- Implementation that treats the spec as inspiration instead of a contract.
- Review comments that mix strategic disagreement with local code nits.
- Abstractions added before the final shape is visible.
- Compatibility paths with no owner, expiry, or deletion story.
