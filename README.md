# Codex System Template

Generic documentation scaffolding for projects that use ChatGPT for planning and review, Codex for implementation and checks, and repo docs as shared memory.

This template is intentionally product-neutral. Replace placeholders with the current project's details, but do not copy project-specific product wording from another project into the generic template.

## Start a New Project

1. Copy this folder into the new project.
2. Fill in the project-specific settings in `AGENTS.md`.
3. Fill in `docs/VISION.md` with the product or project direction.
4. Set the current workflow state in `docs/STATUS.md`.
5. Create or update a feature file in `docs/features/` for any multi-step feature.
6. Use `docs/HANDOFFS.md` when preparing ChatGPT, Codex, review, or follow-up prompts.

Recommended first files to fill in:

- `AGENTS.md`
- `docs/VISION.md`
- `docs/STATUS.md`
- `docs/features/<feature>.md`, when real feature work begins

## Workflow

- Plan before non-trivial implementation.
- Large feature briefs are not build prompts.
- If a prompt has more than 5-7 meaningful implementation requirements, create a Build Pass Plan first.
- Split large work into small, reviewable build passes.
- Each Codex prompt should target one focused implementation outcome.
- Prefer investigation-only first when the repo structure is unknown.
- Related small fixes can be bundled into one local release package when they are safe, local, and easy to review together.
- Review and run relevant checks before committing.
- Commit or push only when explicitly asked.

## Source Of Truth

- `AGENTS.md`: Always-read operating contract for ChatGPT, Codex, and the user.
- `docs/STATUS.md`: Current workflow state, active feature, owner, blockers, and next step.
- `docs/VISION.md`: Durable product or project direction.
- `docs/DECISIONS.md`: Durable product, UX, technical, and workflow decisions.
- `docs/BACKLOG.md`: Not-now work used to prevent scope creep.
- `docs/BUGS.md`: Confirmed bugs, root causes, fixes, and regression memory.
- `docs/HANDOFFS.md`: Reusable prompt, planning, build-pass, review, and follow-up templates.
- `docs/features/*.md`: Feature-specific scope, QA, compatibility rules, implementation notes, release history, and follow-ups.

## Template Rule

Keep this template generic and reusable. Project-specific product language belongs in a copied project instance, not in the base template.
