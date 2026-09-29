---
name: multi-model-dev
description: "Guide project kickoff with multi-model-dev-framework: gather requirements, agree on AI roles and budget, offer context-mode installation, and prepare local inputs and a first task. Use when the user asks to start or configure multi-AI development (多模型协作开发、项目启动配置). Not a general coding skill or an automatic model scheduler."
---

# Multi-Model Dev / 多模型协作启动

Help a developer start a project through one coordinator conversation. Reuse information already supplied; ask only for missing decisions that affect this run. Deliver a small, reviewable kickoff proposal, local project inputs, and the first task handoff. Do not turn kickoff into implementation of the application.

## Load only what is needed

Use the user's language. Confirm a different artifact language only if needed. Read exactly one workflow reference:

- 中文：[项目启动流程](references/kickoff.zh-CN.md)
- English: [Kickoff workflow](references/kickoff.en.md)

Read the matching pair of templates from `assets/` only when drafting project files. This installed skill is self-contained; the framework checkout, Claude and context-mode are not prerequisites. Do not load both languages or a full catalog of skills.

At kickoff, explain context-mode benefits and tradeoffs and obtain an explicit choice: install and verify, skip for now, or verify an existing installation. Reuse a clear choice already given. After opt-in, perform installation and checks with available tools rather than only handing the user commands. Load [中文安装流程](references/context-mode.zh-CN.md) or [English setup](references/context-mode.en.md) only for installation or verification. Record whether package installation, client registration, live tools, and routing are each verified; a required restart is not completed integration.

## Scope and essential boundaries

- Existing project rules and the developer's explicit choices apply. Never infer a project domain from the skill's installation path, another project, or an earlier example.
- The current chat can coordinate only with the user's agreement. A role label does not switch the session's actual model. All models, effort, review and takeover routes are configurable; verify capabilities before execution and never invent CLI IDs.
- Kickoff may create local draft inputs within the requested scope. Only actual developer confirmation changes a draft to confirmed; preserve earlier valid authorization without repeatedly asking. Configuration approval does not by itself authorize application implementation, deployment, publication, or merges.
- This version prepares files and manual handoffs using the host's existing tools. It does not include a scheduler, CLI adapters, MCP server, automatic counters, timers, or a board. Do not launch worker models or claim background work is running as a side effect of kickoff.
- Record planned calls, time, effort and rework assumptions. Unknown token, price, or allowance information stays unknown; do not promise savings or convert tokens into a weekly allowance percentage.
- When the user proceeds to the manual trial, independent review must inspect actual artifacts and evidence. At most 3 revisions follow the initial submission, then the agreed takeover or human decision; no counter reset on session changes. Each Codex run is limited to 25 minutes by a manual stopping plan, not an implemented timer.
- Keep developer inputs local, preserve existing files, and never write project data into this installed skill. Do not alter authentication or repository permissions. Instructions are not a technical permission boundary.

## Completion

Report only the files actually created, the confirmed/pending status, blockers, and the next action. Give the developer a short path to the first trial; avoid dumping the entire internal template into the conversation. No execution or review result exists until it has actually happened.

Bundled templates are distribution copies of the framework's public templates. Keep them in sync when editing the package. The skill is covered by the included [LICENSE](LICENSE).
