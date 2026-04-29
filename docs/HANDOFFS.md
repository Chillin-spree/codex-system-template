# Handoffs

> Reusable prompt, planning, build-pass, review, and follow-up templates for moving work between ChatGPT, Codex, and review.

<!-- Keep templates generic. Add project-specific prompts only when they are reused in this project instance. -->

## Prompt Sizing Rules

- Large feature briefs are not Codex build prompts.
- If a task combines more than 5-7 meaningful implementation requirements, create a Build Pass Plan first.
- A Codex prompt should target one focused implementation outcome.
- Prefer investigation-only first when repo structure is unknown.
- Full feature details belong in `docs/features/<feature>.md`; build prompts should contain only the current pass.
- Bundle related small fixes into one local release package when they are safe, local, and easy to review together.
- Split bundles into focused local passes.
- Do not commit or push between local passes unless explicitly asked.
- Do not bundle unrelated work or high-risk categories just to reduce pushes.

## New-Chat Startup

Use this when starting a new ChatGPT or Codex thread.

```text
We are working on <project>.

Use the repo docs as the source of truth. If pasted history conflicts with repo docs, trust the repo docs and call out the conflict.

Read first, in this order:
- AGENTS.md
- docs/STATUS.md
- docs/features/<active-feature>.md, if docs/STATUS.md lists one
- docs/DECISIONS.md, only when durable decisions matter
- docs/BUGS.md, only for bugfix or regression work

Current task:
<task>

Risk:
Low | Medium | High

Instructions:
- Stay within the current task.
- Prefer the smallest safe change.
- Do not commit or push unless explicitly asked.
- Report any missing context or scope expansion before continuing.
```

## Feature Brief

```text
Task:
Create or refine the feature spec for <feature>.

Context:

Read first, in this order:
- AGENTS.md
- docs/STATUS.md
- docs/VISION.md
- docs/DECISIONS.md, only if relevant
- docs/features/<feature>.md, if it exists

Risk:
Low | Medium | High

Scope:

Non-goals:

Must preserve:

Must not do:

Acceptance:

Report:
- Proposed behavior
- Open questions
- Whether this needs a Build Pass Plan
- Suggested first Codex build prompt, if small enough
```

## Build Pass Plan

Use this when a feature brief is too large for one focused Codex pass.

```text
BUILD PASS PLAN — <feature>

Goal:
<one sentence>

Context:
<what matters from README, AGENTS, STATUS, VISION, DECISIONS, BUGS, and feature files>

Scope:
- <included outcome>

Non-goals:
- <excluded outcome>

Pass breakdown:
1. Investigation / repo map — no edits
2. <focused implementation pass>
3. <focused implementation pass>
4. QA/checks and documentation updates
5. Review polish, if needed

Expected files:
- <files likely to change>

Risks:
- <risk and mitigation>

QA/checks:
- <commands, manual checks, or explicit reason checks are not applicable>

Docs updates:
- <README.md | AGENTS.md | docs/STATUS.md | docs/VISION.md | docs/DECISIONS.md | docs/BACKLOG.md | docs/BUGS.md | docs/HANDOFFS.md | docs/features/<feature>.md | none>

Rollback notes:
- <how to revert or disable safely if needed>

First implementation prompt:
<paste the first focused Codex prompt here>
```

## Codex Implementation Prompt

```text
Task:
Implement <feature/change>.

Context:

Read first, in this order:
- AGENTS.md
- docs/STATUS.md
- docs/features/<feature>.md
- docs/DECISIONS.md, only if relevant
- docs/BUGS.md, only if debugging

Risk:
Low | Medium | High

Build pass:
<pass number and short name>

Not in this pass:
- <excluded work>

Scope:
Current pass only; full feature details belong in the feature file.

Must preserve:
- <behavior, files, APIs, data, or UX that must remain stable>

Must not do:
- <forbidden change>

Acceptance:
- <observable completion criteria>

Checks:
- <automated or manual checks>

Stop and report if:
- scope is ambiguous
- implementation requires risky changes outside this prompt
- required context is missing
- tests reveal unrelated failures
- the change is broader than expected

Report:
- Summary
- Files changed
- Checks run
- Anything blocked or risky
- Recommended next pass, if any
```

## Bug Investigation Prompt

```text
Task:
Investigate <bug/symptom> and identify the smallest safe fix.

Context:

Read first, in this order:
- AGENTS.md
- docs/STATUS.md
- docs/BUGS.md
- docs/features/<feature>.md, if relevant

Risk:
Low | Medium | High

Scope:
Investigate first. Do not edit yet, unless explicitly authorized.

Must preserve:

Must not do:

Acceptance:

Checks:

Stop and report if:
- reproduction is blocked
- required context is missing
- the fix appears broader than expected
- the likely cause is outside the requested scope

Report:
- Reproduction steps
- Likely root cause
- Proposed fix
- Files likely involved
- Whether implementation is safe to proceed
- Proposed fix pass, if implementation is needed
```

## Review Memo

```text
Task:
Review Codex result for <feature/change>.

Context:

Codex summary:

Files changed:

Checks:

Risk:
Low | Medium | High

Acceptance:

Review focus:
- Correctness
- Scope control
- User-visible behavior
- Missing checks
- Documentation updates

Report:
- Approved or not approved
- Required fixes
- Optional follow-ups
```

## Review / Polish Pass

```text
Task:
Apply review polish for <feature/change>.

Context:

Read first, in this order:
- AGENTS.md
- docs/STATUS.md
- docs/features/<feature>.md
- docs/DECISIONS.md, only if relevant

Risk:
Low | Medium | High

Build pass:
Review / polish pass.

Not in this pass:
- New feature scope
- Broad refactors
- Unrelated cleanup

Scope:
Only address review findings, polish, documentation alignment, and check failures needed to complete the accepted scope.

Must preserve:

Must not do:

Acceptance:

Checks:

Stop and report if:
- a requested polish item changes product behavior
- the fix requires broader implementation than expected
- tests reveal unrelated failures

Report:
- What changed
- Files changed
- Checks run
- Remaining risks or follow-ups
```

## Fix Follow-up Prompt

```text
Task:
Apply the requested fix after review.

Context:

Read first, in this order:
- AGENTS.md
- docs/STATUS.md
- docs/features/<feature>.md

Review finding:

Risk:
Low | Medium | High

Scope:
Only fix the reviewed issue unless another change is required to complete it safely.

Must preserve:

Must not do:

Acceptance:

Checks:

Stop and report if:
- scope is ambiguous
- implementation requires risky changes outside this prompt
- required context is missing
- tests reveal unrelated failures

Report:
- What changed
- Files changed
- Checks run
- Any remaining risk
```

## Scope Question

```text
Task:
Resolve a scope or product question before implementation continues.

Context:

Question:

Options:
1.
2.
3.

Risk:

Must preserve:

Decision needed:

Report:
- Chosen direction
- Any change to acceptance criteria
- Whether docs need updating
```

## Documentation Sweep Checklist

Use this before review, release, or handoff when docs may need alignment.

```text
Task:
Perform a documentation sweep for <feature/change>.

Context:

Check these files for needed updates:
- README.md — project entrypoint, setup, source-of-truth map
- AGENTS.md — always-read operating contract and project-specific guardrails
- docs/STATUS.md — current workflow state, active feature, next step, latest handoff
- docs/VISION.md — durable product or project direction
- docs/DECISIONS.md — durable decisions only
- docs/BACKLOG.md — not-now work and deferred scope
- docs/BUGS.md — meaningful bug/root-cause memory
- docs/HANDOFFS.md — reusable prompt/planning templates
- docs/features/*.md — feature-specific scope, QA, compatibility, release history, follow-ups

Rules:
- Do not duplicate detailed feature specs outside feature files.
- Do not put reusable prompt templates outside docs/HANDOFFS.md.
- Keep AGENTS.md concise enough to read every session.
- Update docs/STATUS.md only for current state.
- Update docs/DECISIONS.md only for durable decisions.
- Update docs/BUGS.md only for meaningful root-cause memory.

Report:
- Docs updated
- Docs intentionally left unchanged
- Any source-of-truth conflicts found
```

## Commit / Push Prompt

Use this only when the user explicitly asks to commit or push.

```text
Task:
Prepare and publish the completed work for <feature/change>.

Context:

Read first, in this order:
- AGENTS.md
- docs/STATUS.md
- docs/features/<feature>.md, if relevant

Risk:
Low | Medium | High

Scope:
Commit and/or push only the approved changes for <feature/change>.

Must preserve:
- User work and unrelated files
- Existing branch history unless explicitly instructed otherwise

Must not do:
- Commit unrelated changes
- Rewrite history
- Force push unless explicitly approved
- Push if checks fail without reporting first

Acceptance:
- Working tree reviewed
- Intended files staged
- Relevant checks run or skipped with reason
- Commit message summarizes the approved scope
- Push happens only if explicitly requested

Checks:
- git status
- git diff
- <project checks>

Stop and report if:
- unrelated changes are present
- checks fail
- branch or remote is unclear
- the requested publish action is unsafe

Report:
- Commit created, if any
- Push completed, if any
- Files included
- Checks run
- Any excluded or unrelated work
```

## Refactor Prompt

```text
Task:
Refactor <area> for <specific reason>.

Context:

Read first, in this order:
- AGENTS.md
- docs/STATUS.md
- docs/DECISIONS.md, only if relevant
- docs/features/<feature>.md, if relevant

Risk:
Medium | High

Scope:

Must preserve:
- Current user-visible behavior
- Existing public APIs unless explicitly approved

Must not do:
- Add unrelated behavior
- Rewrite broader areas than scoped
- Change dependencies unless explicitly approved

Acceptance:

Checks:

Stop and report if:
- scope is ambiguous
- implementation requires risky changes outside this prompt
- required context is missing
- tests reveal unrelated failures

Report:
- Refactor summary
- Files changed
- Behavior preserved
- Checks run
- Any follow-up risk
```
