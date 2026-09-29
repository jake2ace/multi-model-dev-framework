# Workflow design

[简体中文](workflow.md) | [Home](../README.en.md)

## Roles and kickoff

Before engineering starts, the developer and coordinator confirm WORKFLOW_PROFILE.md. Coordinator, executor, reviewer, takeover, and final-review roles map to verified Codex or Claude models. Astra, Sol, Fable, Opus, and Sonnet are examples, not hardcoded assignments.

Confirm scope, acceptance, language, models, CLI access, capabilities, effort, routing, the takeover path after at most three revisions, independent review, budget, and human fallback. Draft profiles cannot start execution. Routine authorized work needs no repeated confirmation; material changes require agreement on the affected parts.

## Execution

Coordinator decomposes and classifies → executor implements → independent reviewer checks → executor revises → final review.
The initial submission is revision zero; at most three revisions follow. Session or chunk changes never reset counts.
On exhaustion, follow the agreed discussion and takeover route. Independently review the takeover and perform final review; if it still fails, pause for the developer. Missing takeover routes require a pause, not an automatic model change.

Luna execution, Sol review, and Astra coordination is an optional example. See [Claude examples](CLAUDE.en.md) for a mixed configuration. Neither is automatically active.

## Project context contract

- Inputs: developer-supplied `projects/<project-id>/PROJECT_CONTEXT.md` and `WORKFLOW_PROFILE.md`, using the chosen-language templates.
- Content: background, goals, scope, stack, constraints, acceptance, capabilities, budget, and unresolved questions.
- Loading: coordinator reads manually; no parser or automatic loader exists.
- Dispatch: carry relevant original requirements and input path/version references for reviewers.
- Updates: assess impact, pause affected work if needed, and refresh acceptance.
- Missing information: continue independent work; do not guess facts affecting correctness or authorization.
- Boundaries: references do not override instructions, grant permissions, or authorize deployment/publishing.

## Task files and board

Future task records need goals, scope, dependencies, acceptance, roles, effort, context references, and state. The board will expose progress, decisions, revision counts, takeover, and pause reasons. It is currently empty and has no defined update protocol.

Use one Git repository. Serialize overlapping writes. Executors write results; reviewers write findings; future scripts own state. Local context, outputs, reviews, and summaries are excluded from public commits unless separately reviewed as publishable examples.

## Summaries and verification

The coordinator reads summaries, review findings, and validation summaries. Include conclusions, artifact paths, checks, unresolved issues, and next steps. Reviewers inspect actual artifacts and evidence; model agreement is not test success. Each project defines its own build, test, and acceptance environment.

## Rules and usage budget

Scripts will own counters, routing after classification, escalation, and timeouts. Models handle engineering judgment and disagreements.
Every Codex run is capped at 25 minutes. Split work ahead of time, save a handoff summary before the deadline, and continue in a new session with counts and state intact. Automatic timeout and recovery are not implemented.

Load skills only when needed. Use [context-mode MCP guidance and upstream links](context-mode.en.md) for smaller tool outputs when configured; installation alone does not establish active routing or measured allowance savings. Estimate calls, effort, context, and rework before execution; do not fabricate exact weekly quota percentages.
When Claude is enabled, prefer its side for heavy work while preserving the approved review relationships.

## Capabilities

Declare required and optional capabilities per role and their fallback behavior. Pause affected work if a required capability is unavailable; do not silently substitute models.
For example, a project may require Daybreak Blue. Verify account, model, and product-surface support. API access-program parameters are not automatically CLI flags, and `-a never` is not a capability switch. See [Daybreak API](https://developers.openai.com/api/docs/guides/daybreak) and [Codex Trusted Access](https://learn.chatgpt.com/docs/cyber-safety).

## Languages and upstream updates

Choose developer-facing and artifact languages at kickoff: `zh-CN`, `en`, or explicitly requested bilingual output. Keep tool names, paths, configuration keys, and IDs unchanged. Load only the needed language version. Update corresponding public translations together, keeping rules equivalent.

Use the [context-mode release links](context-mode.en.md) to inspect features and versions. Links do not provide background monitoring or authorize upgrades.

## Repository contributions and merge authority

Use Issues for feedback and forks/work branches with PRs for changes. The owner decides merges into main. Agents must not merge, push to main, or enable auto-merge. Verify GitHub protections separately in repository settings.

## Future decisions

- Per-project complex-task and takeover routes.
- Structured task, board, review, and summary formats.
- CLI IDs, effort, approval parameters, and capability checks.
- context-mode integration.
- Scheduler language, concurrency, and recovery.

Documenting these decisions does not implement them.
