# <feature-name>

> Reusable feature-file template for durable feature scope, QA, compatibility, release history, and follow-ups.

<!--
Status: <status>
Owner: <owner>
Version: <version>
Last updated: <date>

Feature files are the source of truth for durable feature context. Do not duplicate live workflow state from docs/STATUS.md or durable decisions from docs/DECISIONS.md unless the detail is needed to understand this feature.

Use docs/HANDOFFS.md for Build Pass Plans and copy-paste Codex prompts.
-->

## Summary

- **Feature**: <feature-name>
- **Status**: <status>
- **Owner**: <owner>
- **Target version**: <version>
- **Last updated**: <date>
- **Short description**: <one or two sentences describing the user value and feature boundary>

## Current Release State

- **Release status**: planned | in-progress | shipped | paused | obsolete
- **Current pass**: <current build/review/pass state>
- **Shipped in**: <version or none>
- **Related release note**: <link or note>
- **Current known limitation**: <none or short note>

## User-Facing Scope

- <user-visible capability or workflow>
- <user-visible behavior>
- <user-facing constraint or expectation>

## Non-Goals

- <explicitly excluded behavior>
- <future idea that should not be built in this feature>
- <adjacent system or workflow that remains unchanged>

## Compatibility / Preservation Rules

- Preserve <existing user behavior, data, API, file format, or workflow>.
- Do not break <compatibility surface>.
- Maintain compatibility with <supported environment, integration, or version>.
- If compatibility cannot be preserved, stop and document the decision needed before implementation continues.

## Implementation Notes

- <important files, modules, or systems involved>
- <architecture or sequencing note>
- <known constraint for implementers>
- <link to relevant decision, if needed>

Keep this section focused on durable feature context. Full build prompts, pass plans, and review prompts belong in `docs/HANDOFFS.md`.

## QA Checklist

- [ ] <primary user flow works>
- [ ] <edge case or regression check>
- [ ] <compatibility or preservation check>
- [ ] <relevant automated check or reason not applicable>
- [ ] <documentation updated or intentionally unchanged>

## Risks

- **Risk**: <risk>
  - **Impact**: <impact>
  - **Mitigation**: <mitigation>

- **Risk**: <risk>
  - **Impact**: <impact>
  - **Mitigation**: <mitigation>

## Release History

<!-- Most recent first. Keep entries concise. -->

### <date> — <version> — <status>

- **Summary**: <what changed>
- **Commit**: <commit>
- **QA**: <checks run or skipped with reason>
- **Notes**: <release or review note>

## Open Follow-Ups

- [ ] <follow-up item>
- [ ] <deferred improvement>
- [ ] <question or decision needed>
