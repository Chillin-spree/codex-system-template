# <feature-name>

> Durable feature record for scope, build passes, QA, release history, and follow-ups.

<!--
Status: <status>
Owner: <owner>
Version: <version>
Last updated: <date>

Feature files are the source of truth for durable feature context. Keep live workflow state in docs/STATUS.md and reusable prompt templates in docs/HANDOFFS.md.

Use docs/HANDOFFS.md for Build Pass Plans and copy-paste Codex prompts.
-->

## Summary

- **Feature**: <feature-name>
- **Status**: <status>
- **Owner**: <owner>
- **Target version**: <version>
- **Last updated**: <date>
- **User outcome**: <one or two sentences describing the user value and feature boundary>

## Current State

- **Status**: planned | in-progress | shipped | paused | obsolete
- **Current pass**: <current build/review/pass state or none>
- **Next pass**: <next focused pass or none>
- **Shipped in**: <version or none>
- **Known limitation**: <none or short note>

## Scope

- <user-visible capability or workflow>
- <user-visible behavior>
- <user-facing constraint or expectation>

## Out Of Scope

- <explicitly excluded behavior>
- <future idea that should not be built in this feature>
- <adjacent system or workflow that remains unchanged>

## Preservation Rules

- Preserve <existing user behavior, data, API, file format, or workflow>.
- Do not break <compatibility surface>.
- Maintain compatibility with <supported environment, integration, or version>.
- If compatibility cannot be preserved, stop and document the decision needed before implementation continues.

## Build Passes

<!-- Keep this as pass history and next-pass planning, not full prompt text. Use docs/HANDOFFS.md for copy-paste prompts. -->

- **Pass 1**: <name/status/result>
- **Pass 2**: <name/status/result>
- **Next pass**: <small focused outcome or none>

## Implementation Notes

- <important files, modules, or systems involved>
- <architecture or sequencing note>
- <known constraint for implementers>
- <related decision, if needed>

## Acceptance / QA

- [ ] <primary user outcome works>
- [ ] <important edge case or regression check>
- [ ] <compatibility or preservation check>
- [ ] <relevant automated check or reason not applicable>
- [ ] <documentation updated or intentionally unchanged>

## Risks / Open Questions

- **Risk**: <risk>
  - **Impact**: <impact>
  - **Mitigation**: <mitigation>

- **Question**: <decision or clarification needed>
  - **Owner**: <owner>
  - **Needed by**: <pass, milestone, or date>

## Release History

<!-- Most recent first. Keep entries concise. -->

### <date> — <version> — <status>

- **Summary**: <what changed>
- **Commit**: <commit>
- **QA**: <checks run or skipped with reason>
- **Release note**: <user-facing note or none>

## Open Follow-Ups

- [ ] <deferred improvement>
- [ ] <bug, polish, or compatibility follow-up>
- [ ] <documentation or release follow-up>
