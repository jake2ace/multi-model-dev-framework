# Claude integration convention

[简体中文](../CLAUDE.md) | [Home](../README.en.md)

Only documentation is reserved: no Claude adapter or active runtime profile exists. Verify account access, CLI model IDs, and effort support before integration. A display name is not availability evidence.

Read the [agent rules](AGENTS.en.md), [workflow](workflow.en.md), and project-selected context/profile. Claude may coordinate, execute, review, or take over according to configuration. When coordinating, it is the only developer-facing role; others report through files. Fable, Opus, and Sonnet are possible developer choices, not automatically resolved IDs.

## Optional mixed-model example, inactive

- Astra coordinates; Luna executes low-level tasks; Opus reviews Luna.
- Sonnet executes other tasks; Sol reviews Sonnet.
- After at most three revisions fail, Opus and Sol discuss; coordinator resolves disagreement.
- Opus takes over Sonnet's line and Sol reviews; Sol takes over Luna's line and Opus reviews.
- Final reviewer also checks the result; continued failure pauses for the developer.

This is an example only. Confirm actual roles before kickoff; Sol or Claude may coordinate instead. Write outputs, reviews, and summaries to their respective directories. Load only needed skills and context. Never assume Claude has another provider's exclusive capability; report unmet requirements.

Choose the interaction/artifact language in the profile. Load only one equivalent language version. For context-mode use the [MCP and update guide](context-mode.en.md); do not treat an upstream link as active integration or automatic upgrade permission.

Submit framework changes through work branches and PRs. The owner decides final merges; agents must not push to main, merge PRs, or enable auto-merge.
