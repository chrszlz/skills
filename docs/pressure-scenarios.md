# Pressure Scenarios

Use these prompts to forward-test the skills with fresh context. The goal is to see whether the skill changes behavior, not whether the agent can infer the desired answer from this repo.

## Entry Routing

```text
I need to add a nullable `note` field to the Upload model and show it on the detail screen, mirroring the existing `caption` field. Should this go through the full spec-first motion, a combined lightweight pass, or straight to implementation?
```

Expected pressure: the agent should apply the concrete routing rubric instead of reflexively running the full pipeline, verify the "just like caption" analogy before deciding, and choose the lightweight or skip path for a small, pattern-covered, reversible change.

## `write-spec`

```text
Use $write-spec to turn this idea into a spec: our app has three slightly different retry flows for background uploads. I want to add a fourth flow for a new import path.
```

Expected pressure: the skill should push on whether a fourth flow is the right solve, map the existing retry concepts, compare reuse versus a new path, and produce an implementation-ready spec.

## `challenge-spec`

```text
Use $challenge-spec to review this spec. I am worried it might be a local hack, but I also need the feature soon. Focus on whether the system already has a better place for this behavior.
```

Expected pressure: the skill should be constructive and slightly adversarial. It should ask whether the change deserves to exist, identify simpler alternatives, and avoid generic risk lists.

## `refine-spec`

```text
Use $refine-spec to incorporate these review comments into the spec. Some comments disagree with each other; preserve the decision record and make the final plan clear enough to implement.
```

Expected pressure: the skill should classify feedback, resolve contradictions explicitly, tighten non-goals, and leave a clean mergeable doc.

## `implement-spec`

```text
Use $implement-spec to build from this accepted spec. If the codebase disagrees with the plan, stop and explain the mismatch instead of inventing a new approach.
```

Expected pressure: the skill should preflight the spec against code reality, implement in slices, verify targeted behavior, and avoid silent divergence.

## `review-diff`

```text
Use $review-diff to review this implementation PR against the accepted spec. Prioritize behavioral bugs, missing tests, and places where the code violates the plan.
```

Expected pressure: the skill should produce findings first, grounded in files or behavior, and separate correctness concerns from taste.

## `simplify-diff`

```text
Use $simplify-diff on this working implementation. The tests pass, but I suspect the diff has too much abstraction and a compatibility path that may not need to exist.
```

Expected pressure: the skill should preserve behavior, look for deletion and localization opportunities, and recommend or apply simplifications without reopening product strategy.
