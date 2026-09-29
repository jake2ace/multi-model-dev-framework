# Project workflow profile

[简体中文](WORKFLOW_PROFILE.md)

> Complete with the developer before engineering starts. No automatic loader exists. Blank fields are not approval. Do not include passwords, API keys, or tokens.

## Status and sources

- Profile version: TBD
- Project context path and version: TBD
- Status: draft / confirmed (currently draft)
- Developer confirmation record and time: TBD
- Interaction language (`zh-CN` / `en` / bilingual): TBD
- Artifact language (`zh-CN` / `en` / bilingual): TBD

## Role mappings

For each role, record display name, provider, CLI model ID, effort (specified or coordinator-selected), and verified availability.

| Role | Model / provider / CLI ID | Effort | Availability |
| --- | --- | --- | --- |
| Coordinator / decision maker | TBD | TBD | Unverified |
| Low-level executor | TBD | TBD | Unverified |
| Low-level reviewer | TBD | TBD | Unverified |
| Other-level executor | TBD | TBD | Unverified |
| Other-level reviewer | TBD | TBD | Unverified |
| Final reviewer | TBD | TBD | Unverified |

Coordinator choices may include Codex Astra / Sol or verified Claude Fable / Opus / Sonnet. Nothing is enabled by this template. If one model fills multiple roles, disclose session separation and review limitations for the developer to decide.

## Routing and failure handling

- Classification criteria and routes: TBD
- Maximum revisions after initial submission: 3
- Roles discussing exhausted revisions: TBD
- Takeover executor for each route: TBD
- Independent reviewer after takeover: TBD
- Continued failure after takeover: pause for the developer
- Missing takeover or required capability: pause affected tasks for the developer

## Capabilities and execution

- Required / optional capabilities by role: TBD
- Verification method and evidence: TBD
- CLI / adapter: TBD
- Write scope and concurrency rules: TBD
- context-mode required / optional / disabled: TBD
- context-mode tool and hook verification, summary approach: TBD
- context-mode upstream updates: https://github.com/mksglu/context-mode/releases/latest
- Codex run limit: 25 minutes; chunking and handoff: TBD

## Budget and kickoff

- Call and allowance estimate with assumptions: TBD
- Over-budget handling: TBD
- Developer has confirmed roles, language, routing, effort, acceptance, capabilities, escalation, budget: unconfirmed
- Remaining kickoff blockers: TBD

Only record confirmation after the developer actually confirms. This agreement covers the listed project scope, not automatic publishing or deployment.
