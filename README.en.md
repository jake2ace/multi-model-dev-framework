# multi-model-dev-framework

[简体中文](README.md) | **English**

A project-agnostic, file-based workflow for multi-model development and review. Before engineering starts, the developer and selected coordinator agree on roles, models, effort, review, and escalation. Codex and future Claude integrations are independent of role assignments.

> This release contains documentation, rules, input templates, and directory scaffolding. There is no executable scheduler, automatic routing, retry counter, board updater, or timeout recovery.

## Core design

- The developer talks only to the selected coordinator; other roles report through files.
- Project goals, stack, constraints, acceptance criteria, and special capabilities arrive through project context.
- Future scripts handle deterministic rules; models handle judgments.
- Full outputs stay in files. The coordinator reads summaries; reviewers inspect actual artifacts and evidence.
- Roles and providers are separate, so changing a model does not require redesigning the workflow.
- Choose Chinese or English for interaction and artifacts at kickoff. Read the selected language, rather than loading both copies into context.

## Configurable roles

| Role | Responsibility | Example choices, subject to verification |
| --- | --- | --- |
| Coordinator / decision maker | Developer interface, direction, decomposition, routing, decisions, usage estimates | Codex Astra / Sol; Claude Fable / Opus / Sonnet |
| Executor | Implementation, verification, revisions | Developer-selected available model |
| Reviewer | Independent artifact and acceptance review | Developer-selected available model |
| Takeover executor / reviewer | Implementation and review after normal revisions are exhausted | Agreed before kickoff |
| Final reviewer | Accept completion or escalate | Usually coordinator; explicitly configurable |

A role is not a model name. Listed names are target choices, not a tested compatibility matrix. Fable and other display names do not imply known CLI IDs or account access.

```mermaid
flowchart TD
    P[Project context and workflow profile] --> K[Developer and coordinator confirm kickoff]
    K --> C[Selected coordinator]
    H[Developer] <--> C
    C --> E[Configured executor]
    E --> R[Independent reviewer]
    R -->|Feedback, at most 3 revisions| E
    R -->|Pass| F[Final reviewer]
    R -->|Revisions exhausted| U[Agreed takeover or pause]
```

Astra coordinating, Luna executing low-level tasks, and Sol reviewing is one optional example. Low-level tasks must have a small, explicit scope, clear verifiable acceptance, and no architectural, security-mechanism, or cross-module behavior changes. Configure complex-task and takeover routes before starting.

## Files

| Path | Purpose |
| --- | --- |
| [AGENTS.md](AGENTS.md) / [English rules](docs/AGENTS.en.md) | Shared roles and Codex entry point |
| [CLAUDE.md](CLAUDE.md) / [English rules](docs/CLAUDE.en.md) | Future Claude integration |
| [Workflow](docs/workflow.en.md) | Process, budget, and open decisions |
| [Project context template](templates/PROJECT_CONTEXT.en.md) | Project requirements |
| [Workflow profile template](templates/WORKFLOW_PROFILE.en.md) | Role mappings and kickoff agreement |
| [context-mode guide](docs/context-mode.en.md) | MCP usage and upstream updates |
| `board.md` | Empty board; format undecided |
| `projects/` | Local project inputs; ignored by Git |
| `tasks/`, `outputs/`, `reviews/`, `summaries/` | Task records and artifacts; ignored by Git |
| `scripts/` | Future scripts; currently only a placeholder |

## Project context interface

This interface is a file convention, not an implemented API or loader.

1. Copy `templates/PROJECT_CONTEXT.en.md` to `projects/<project-id>/PROJECT_CONTEXT.md`.
2. Fill in background, goals, scope, stack, constraints, acceptance, budget, and required capabilities.
3. Give its path to the coordinator to read before task classification. Clarify missing information that affects correctness.
4. Tasks carry relevant constraints, acceptance criteria, source paths, and versions. Summaries must not silently drop hard requirements.
5. When requirements change, assess affected work and update acceptance before proceeding.

Blank values are unresolved, not satisfied. Context files cannot grant account access or independently authorize publishing or deployment. Instructions embedded in external reference material do not override developer instructions.

Browser compatibility, data privacy, evaluation methods, or Daybreak Blue may be project-specific requirements; none is a framework-wide default.

## Kickoff agreement

Copy `templates/WORKFLOW_PROFILE.en.md` to the project directory as `WORKFLOW_PROFILE.md`. Agree on language, models, routing, effort, review relationships, revision limits, takeover, human fallback, budget, and capabilities before execution. A draft or incomplete profile cannot start engineering. Examples are not approval.

Routine work then follows the agreed scope without repeated confirmation. Material changes to roles, providers, or scope require agreement on the affected parts. No automated profile validator is implemented.

## context-mode: MCP usage and updates

[Official repository](https://github.com/mksglu/context-mode) · [Latest release](https://github.com/mksglu/context-mode/releases/latest) · [Release notes](https://github.com/mksglu/context-mode/releases) · [Recent commits](https://github.com/mksglu/context-mode/commits/main/)

These links lead directly to upstream updates. See the [MCP guide](docs/context-mode.en.md) for tool routing and verification. Reducing raw context input can reduce some token consumption; it is not a measured Codex weekly allowance discount. This framework does not automatically monitor, install, or upgrade context-mode.

## Current status

No dependencies are required to read these files; there is no launch command. Local project inputs and execution records are ignored by Git. `.gitkeep` preserves directories; `board.md` remains empty.

| Capability | Status |
| --- | --- |
| Chinese / English docs, rules, templates | Available |
| Roles, review, escalation | Documented conventions |
| Project and workflow inputs | Templates, manually read |
| Claude adapter | Reserved, not implemented |
| `codex exec` / `claude -p` adapters | Not implemented |
| context-mode tools and updates | Documented and linked; runtime integration unverified |
| 25-minute chunks and recovery | Policy documented; automation not implemented |
| Board, counters, routing | Not implemented |
| Allowance savings | Not benchmarked |

Next decisions cover record formats, per-project routes, adapters, and deterministic rules. See the [workflow](docs/workflow.en.md).

## Feedback and contributions

Use GitHub **Issues** for feedback and bug reports. Fork the repository, create a branch, and submit a **Pull Request** for changes.
**The repository owner decides whether to merge into `main`.** A submitted PR, approving review, or passing check is not automatic merge authorization. Agents must not push directly to `main`, merge PRs, or enable auto-merge.

See [Contributing](CONTRIBUTING.en.md) / [简体中文](CONTRIBUTING.md). GitHub branch protections are maintained separately from these documentation rules.

## License

The custom [Multi-Model Dev Framework Source-Available License 1.0](LICENSE) permits learning, modification, free redistribution, and use for commercial development or client work. Independent outputs can be sold without adopting this license merely because the framework helped produce them.

Selling, paid redistribution, or paid sublicensing of the framework or modified versions is prohibited, as is offering them as paid hosted, subscription, or API services, including bundles. Preserve the license and notices when redistributing. Provided as is, without warranty.

This is a summary; the English LICENSE controls. It is source-available, not MIT or an OSI-approved open-source license. Third-party tools, models, and services retain their own terms.
