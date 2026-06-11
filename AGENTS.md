# Skills Repo Agent Guide

This repository contains generic workflow skills for spec-first engineering. Keep the repo useful across projects and teams; put project-specific policy in the project that owns it.

## Contribution Rules

- Use lowercase hyphen-case names, preferably short verb-led phrases such as `write-spec`.
- Each skill folder must contain `SKILL.md` and `agents/openai.yaml`.
- Do not add per-skill README files.
- Add `scripts/`, `references/`, or `assets/` only when they materially reduce repeated work or context load.
- Keep `SKILL.md` concise. Prefer direct procedures, checklists, and quality bars over long essays.
- Frontmatter must contain only `name` and `description`.
- Descriptions should start with `Use when...` and describe trigger conditions, not the whole workflow.
- Default prompts in `agents/openai.yaml` must mention the skill with `$skill-name`.

## Skill Ethos

These skills exist to make engineering judgment more repeatable:

- Treat specs as real artifacts, not preambles to code.
- Challenge whether the proposed change should exist.
- Prefer system fit over local cleverness.
- Improve surrounding systems when repeated one-offs reveal a missing abstraction.
- Avoid boiling the ocean; choose the smallest durable improvement.
- Separate implementation review from simplification. Finding risk and improving shape are related, but not identical.

## Validation

Run the skill validator on every changed skill:

```sh
python3 /Users/chris/.codex/skills/.system/skill-creator/scripts/quick_validate.py ./skill-name
```

For larger changes, forward-test with prompts from `docs/pressure-scenarios.md`. Validate behavior from outputs, not from assumptions about what the skill should have done.

## Local Authoring Notes

Use the official scaffold for new skills:

```sh
python3 /Users/chris/.codex/skills/.system/skill-creator/scripts/init_skill.py skill-name --path /Users/chris/code/skills
```

When updating `agents/openai.yaml`, keep `display_name`, `short_description`, and `default_prompt` aligned with `SKILL.md`.
