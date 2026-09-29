# First run: from setup to one small task

[简体中文](quickstart.md) | [Back to README](../README.en.md)

Prepare two files, agree on assignments with your coordinator, and try one small task. You do not need to study scheduler internals or install every model and MCP server first.

**This version requires manual handoffs and record keeping.** The repository does not start other AIs, select models, or update a board automatically. The prompts below guide existing AI tools; they are not launch commands.

Prefer having the AI gather requirements and fill the inputs? Start with [skill installation and testing](skill.en.md). The steps below remain available for manual use without the skill.

## 1. Prepare a local working copy

You need Git and AI coding tools you are authorized to use. Check that the coordinator, executor, and reviewer can access the target project and task files. This framework does not sign you in or provision models.

Run these terminal commands. If you already have a copy, enter its directory and start at `mkdir`:

```sh
git clone https://github.com/jake2ace/multi-model-dev-framework.git
cd multi-model-dev-framework
mkdir -p projects/my-project
cp templates/PROJECT_CONTEXT.en.md projects/my-project/PROJECT_CONTEXT.md
cp templates/WORKFLOW_PROFILE.en.md projects/my-project/WORKFLOW_PROFILE.md
```

Replace `my-project` with your project ID if desired. This directory holds collaboration inputs. Your application code can stay in another local Git repository; record its path in the project context. Do not overwrite that project's existing `AGENTS.md` or `CLAUDE.md` with framework files.

Use these English templates or the [Chinese guide](quickstart.md). You do not need to copy or load both languages.

## 2. Fill in what you know; ask the coordinator to help resolve the rest

| File | Information to prepare first |
| --- | --- |
| `PROJECT_CONTEXT.md` | Goal, code location, allowed changes, acceptance criteria, hard constraints |
| `WORKFLOW_PROFILE.md` | Available models, coordinator/executor/reviewer, effort, budget, failure handling |

Keep unknowns pending; explicitly mark inapplicable fields as none. For a small trial, you can state “low-level tasks only; pause other tasks.” If no takeover model is available, choose “pause for the developer when revisions are exhausted.” Do not enable more models just to fill every row.

Paste this into your selected coordinator session, replacing the angle-bracket placeholders:

```text
I want to use multi-model-dev-framework for one small task.
Local framework path: <path>
Local target project path: <path>
Project context: <framework path>/projects/my-project/PROJECT_CONTEXT.md
Workflow profile: <framework path>/projects/my-project/WORKFLOW_PROFILE.md

Goal: <one-sentence goal>
Models I can actually use: <available models>
Run budget: <time, calls, or usage limit; estimate first if uncertain>

Read the English README, docs/AGENTS.en.md, docs/workflow.en.md,
and the two input files. If using Claude, also read docs/CLAUDE.en.md.
Check missing inputs, model availability, and existing target-project rules.
Help complete the inputs. Give me a short kickoff proposal covering
acceptance, roles and effort, estimated calls, and stopping conditions.
Keep unverified items pending; do not invent model IDs or permissions.
Wait for my configuration confirmation before execution.
Do not independently deploy, publish, or merge code.
```

**Done for this step:** both inputs contain the information needed for this run, you have actually confirmed the profile, and no relevant execution blockers remain. Filling files does not start a task or grant AI account access.

## 3. Manually try one small task

Example: **complete the installation and usage section of an existing CLI tool's README.** Allow changes only to that README. Acceptance: instructions match the actual entry point, no invented arguments, and example commands are verified or explicitly marked unverified.

Substitute your own small task with an easily checkable result. A small trial makes review and handoff overhead easier to see.

1. **Coordinator writes the task.** Include scope, acceptance, executor/reviewer, effort, estimated calls, and stopping conditions. Example file: `tasks/T001.md`.
2. **Arrange an execution session.** In your existing tool, manually open the agreed execution model session and provide the task file and relevant constraints. The executor saves the result or code-diff location, verification evidence, and summary.
3. **Arrange a separate review session.** Give the agreed reviewer the original task, actual artifacts, and evidence. It records pass/changes requested, specific issues, and evidence; the executor summary alone is insufficient.
4. **Return results to the coordinator.** Keep decisions in your coordinator conversation. It reads the execution summary and review conclusion, then arranges revisions or final review. Manually transfer file paths instead of repeating the entire background in every session.
5. **Record the conclusion.** At most 3 revisions follow the initial submission. Track them manually without resetting between sessions. On exhaustion, follow the agreed takeover route or pause. Takeover still requires independent and final review; another failure goes to you for a decision.

These paths can keep records separate. **They are naming examples, not an automated file protocol:**

```text
tasks/T001.md             Goal, constraints, acceptance, assignments
outputs/T001.md           Full result and verification evidence locations
reviews/T001.md           Review feedback and revision count
summaries/T001.md         Short progress update for the coordinator
```

Keep code changes on a working branch in the target project and reference the files/commits in your records. Do not let two execution sessions edit the same file concurrently. Each Codex run is limited to 25 minutes; manually track time, split work early, and save a handoff summary.

**A completed trial has:** an actual artifact, inspectable acceptance evidence, independent review, and a final review conclusion. A PR or passing check does not authorize merging. The framework repository owner still decides merges into its `main`.

## 4. Ask the coordinator for only the key progress information

Use this short summary format if useful. It is not an implemented dashboard:

```text
Task: <ID and goal>
Progress: <completed work / current step>
Quality: <check results, evidence locations, unverified items>
Usage: <known calls and time; source and units for other metrics>
Rework: <initial submission / revision number, at most 3>
Next: <continue / decision needed from me and why>
```

`board.md` is currently empty. Read summaries and reviews for the first trial. Automated board updates, counters, and recovery are future work.

## How to check whether it saves usage and time

The maintainer will refine assignments and effort through real trials. You can compare a single-model run with a multi-model run under the same acceptance criteria before adopting a more elaborate setup.

| Record | Why it matters |
| --- | --- |
| Task, starting revision, and acceptance criteria | Compare equivalent difficulty and quality requirements |
| Models, effort, and context-mode usage | Identify the condition you changed |
| Total elapsed time and human handoff time | Include coordination and review overhead |
| Calls per role and revision counts | Reveal extra consumption from repeated review |
| Available usage metrics with source and units | Keep tokens, fees, and subscription allowance separate; mark unknowns |
| Acceptance results, missed issues, and manual repairs | Avoid trading quality for apparent savings |

Run from the same starting revision without reusing the other run's solution. Record confounders such as caching and other background tasks. One experiment describes one case; collect several representative tasks before generalizing. Without billing attribution, do not convert account allowance changes or token differences into exact per-task saving percentages.

context-mode is optional. Complete a basic trial first, then follow its [guide](context-mode.en.md) to verify tools and statistics and compare whether it helps. Viewing the [latest upstream release](https://github.com/mksglu/context-mode/releases/latest) does not mean it is installed or enabled locally.

## Common blockers

| Situation | Next step |
| --- | --- |
| Looking for a start button or launch command | There is no scheduler yet; follow this manual guide |
| Unsure which models or effort to choose | Give the coordinator actual available models and a budget; confirm its proposal |
| Only one model is available | Separate sessions can trial the process, with agreed review-independence limitations; do not call it cross-model review |
| A model cannot access the project or task files | Resolve paths and access before asking it to reason from incomplete summaries |
| context-mode is unavailable | Follow the agreed fallback if optional; pause affected tasks if required |
| Budget is exceeded or work repeatedly fails | Pause at the agreed limit; have the coordinator explain options instead of silently increasing budget or retrying forever |

Keep real project inputs, execution records, and credentials out of the public repository. Share sanitized onboarding problems or trial findings through [Issues](https://github.com/jake2ace/multi-model-dev-framework/issues).
