# Project kickoff workflow

## Start with a short conversation

Briefly explain that you will help agree on the goal, model assignments, and budget. Reuse supplied facts instead of making the user fill out a long form again.

When information is missing, prioritize the goal and first-version features, users, existing/new project location, available models, and budget. Group only the most consequential missing inputs, usually 1–3 questions at a time, and resolve the rest alongside the proposal.
If stack, effort, or budget is unknown, recommend an option with a reason and mark it pending. Do not turn every template field into a mandatory first-round question.

For discussion-only requests, stay in the conversation. A kickoff request permits local draft preparation within scope. If the location is unknown, work on the proposal first and establish the destination before writing.

## Present a concrete kickoff proposal

Inspect the selected project's existing rules and file state. A new project does not inherit the current chat directory's engineering context; do not create an application in an unspecified directory.

Show a short proposal covering:

1. Goal, included/excluded scope, and verifiable acceptance criteria.
2. Models and effort for coordinator, executor, independent reviewer, and final reviewer. Distinguish proposed from verified assignments; do not claim the current session switched models.
3. First task, handling of complex tasks, takeover, and stopping conditions.
4. Call estimate with assumptions, time or user-specified budget, and whether context-mode is needed.

A minimal trial can use coordinator, executor, and independent review roles, with the coordinator doing final review. This is a proposal for confirmation, not a requirement for three different models or particular providers.
With one model, separate sessions can trial the process; disclose the limitation rather than claiming cross-model review. Codex-only users do not need Claude. Unconfigured complex tasks can pause instead of requiring more models just to fill rows.

A call estimate can describe “one execution + one independent review; each revision adds one execution + one review,” up to 8 execution/review calls. Coordinator conversation, final review, continuation chunks, and takeover are additional. These are planning units, not exact product billing units. Do not invent weekly allowance percentages.

At most 3 revisions follow the initial submission. On exhaustion, follow agreed discussion/takeover; pause for the developer if no takeover is available. Takeover still needs independent and final review; another failure goes to the developer. Pause sooner when the budget runs out.
Each Codex run is limited to 25 minutes; plan chunks and save summaries early. Explain that timing is manual. Special capabilities are project-specific; naming them does not enable them.

## Offer context-mode explicitly

Briefly explain that large logs/files may contribute less raw text to context, at the cost of runtime dependencies, configuration maintenance, possible latency, and local index storage. Small tasks may not benefit; subscription savings are not guaranteed.
Ask the user to choose install and verify / skip for now / already installed, check only, recording client and local/global scope. Reuse an existing choice; an unanswered choice stays pending.
For installation or checking, load the [setup workflow](context-mode.en.md) on demand and perform authorized steps with tools, rather than handing the user commands. Record required restart/trust actions as pending and resume verification afterwards.

## Generate local inputs

Use the [project template](../assets/PROJECT_CONTEXT.en.md) and [workflow profile](../assets/WORKFLOW_PROFILE.en.md). Fill them from the conversation; the user confirms key decisions. Remove template-language navigation that would be broken in the generated copies.

Use a developer-specified record location when provided. Otherwise, once the target path is established, propose `<target-project>/.multi-model-dev/<project-id>/` for local inputs. This is a records directory, not application source or the skill installation directory.

- Inspect before writing. Preserve user content, versions, and valid confirmations in existing inputs; never replace existing AGENTS.md / CLAUDE.md.
- If ignore protection is missing, add a `.gitignore` containing `*` inside a new `.multi-model-dev/` directory to protect local records. Read and preserve any existing file before editing. In Git projects, check actual input files with `git check-ignore`. Forced additions can bypass ignores; do not promise files can never be uploaded.
- Name the generated files `PROJECT_CONTEXT.md` and `WORKFLOW_PROFILE.md`, use relative references between them, and clearly record the target source directory.
- Mark unknowns pending and inapplicable items none. Limit this run's scope and distinguish current blockers from future fields.
- Record confirmed status only after the developer accepts the presented profile, including time and a short confirmation source. Do not store full conversations or private account details.
- Do not ask again for unchanged valid approval. Confirm only material changes to roles, budget, or scope.

When the user requests a trial and the profile is executable, prepare `tasks/T001.md` inside the records directory: goal, allowed files, dependencies, original acceptance and constraints, input versions, roles/effort, budget, stopping conditions, and status. Continue existing numbering without overwriting or resetting tasks.
Create directories as needed; no empty logs or fabricated results. Kickoff does not call model accounts or change permissions. Install context-mode only after the user chooses it, following the dedicated setup workflow.

## Hand off the first task

Provide short copyable prompts for the executor and reviewer, referring to the task file and target project. Execution must produce actual artifacts and verification evidence; review must inspect the original task, actual changes, and evidence.
Use this run's `outputs/`, `reviews/`, and `summaries/` for records. Summaries include conclusions, paths, verification, unresolved issues, and next steps. Execution prompts preserve scope; review prompts request specific findings and a pass/changes-requested conclusion.

In this version the user manually opens the agreed sessions in existing AI tools and transfers paths; decisions still go through the coordinator. Do not run the generated prompts and pretend a second model has started.
If automation is separately requested, explain that this package has no scheduler and establish actual available execution mechanisms and authorization. Do not silently build a new scheduler.

Finish with at most five focus areas: goal/acceptance, assignments, budget/stops, quality/revision count, and next action/blockers. Unrun work is unrun; a confirmed profile is not a completed project.

## Optional context-mode and trial records

Discover actual MCP tools only when the user chooses context-mode. For large outputs, use applicable `ctx_execute` / `ctx_batch_execute` or indexing/retrieval tools; follow host-exposed definitions and parameters. Use `ctx_doctor` and `ctx_stats` when available; readable stats do not prove active hooks.
If required but unavailable, block affected tasks; if optional, follow the confirmed fallback. This skill does not depend on context-mode. After opt-in, perform installation and verification; do not upgrade or monitor by default.
[Upstream guide](https://github.com/mksglu/context-mode) · [Latest features and release](https://github.com/mksglu/context-mode/releases/latest).

After a trial, record per-role calls, elapsed time, human handoff time, revisions, and acceptance. Keep tokens, fees, and subscription allowance separate with sources and units; leave unknowns unknown. Compare configurations under equivalent acceptance criteria without claiming unmeasured savings.
