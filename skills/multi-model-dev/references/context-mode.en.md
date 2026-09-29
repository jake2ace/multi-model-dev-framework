# context-mode: opt-in installation and verification

## Offer a clear choice with a short explanation

Offer the choice during kickoff; silence is not consent. Reuse an explicit choice already given.

- **Benefits:** large files, logs, and batch searches can return relevant results instead of all raw text, potentially reducing input and repeated reading.
- **Tradeoffs:** runtime dependencies and client configuration need maintenance; processing can add latency and may not pay off for small tasks. Local indexes/session records may need disk and private-data management. Hook support varies by client version.
- **Evidence:** no guaranteed subscription saving or speed improvement; upstream marketing percentages are not this project's measurements.
- **Scope:** install local context-mode for the selected client, potentially with MCP and hooks. This does not install every provider or connect optional external analytics.

Example question: “Would you like context-mode for this client: install and verify / skip for now / already installed, check only? It can help with large outputs, but adds dependencies and maintenance, and actual savings need testing.”
Give a task-specific recommendation, without selecting installation by default. If skipped, record it and continue normal kickoff without repeatedly trying to persuade the user.

## After opt-in, perform the available installation steps

1. **Identify the target:** establish client, runtime machine/container, and configuration scope. Inspect existing plugins/MCP entries, versions, and tools to avoid duplication. A local `.claude` or `.codex` directory alone does not establish the intended client.
2. **Check current upstream instructions:** read the [official installation guide](https://github.com/mksglu/context-mode#install), [releases](https://github.com/mksglu/context-mode/releases/latest), and installed client help. Verify dependencies for the selected version; main docs may differ from the released package. Record actual version/commit and source rather than promising a permanently supported version.
3. **Preserve rollback information:** back up only files being changed outside public repositories. Report backup paths, not entire configs that may contain credentials. Prefer native registration tools and preserve unrelated MCP servers, plugins, hooks, and project rules. Verify a healthy existing installation instead of silently upgrading it.
4. **Install and register:** actually execute the supported setup using available tools. The installation choice authorizes ordinary steps within the explained scope; do not ask again for every command. Before adding an unapproved runtime, expanding scope or permissions, or resolving a conflict destructively, explain the specific change and obtain authorization. Do not repeat approval for already disclosed and authorized dependencies or ordinary setup steps. Respect host approval controls.
5. **Verify:** use the layers below. A tutorial or download link alone is not completion. If a restart or user trust action is required, save a continuation note and report “awaiting restart/trust,” then verify in the next session. Do not forcibly close the user's active work.

Authorization covers the explained local integration. Do not change authentication, weaken approvals, enable external analytics uploads, install unrelated clients, or delete existing indexes. On failure, report the concrete diagnosis and roll back only this run's changes if needed; do not retry indefinitely.

## Select the client route

**Codex:** inspect `codex plugin --help`. Upstream currently provides a marketplace plugin path, usable through available native installation tools or supported CLI commands. Where supported, use `codex plugin marketplace add mksglu/context-mode`, inspect the actual listed plugin identity, and install with the syntax from `codex plugin add --help`. Adding a marketplace is not installing the plugin. If only a supported UI route exists, use authorized computer interaction rather than inventing a private API.

Verify hook flags and trust requirements against current client capabilities. Reachable MCP tools do not establish working hooks. Explain existing plugin/manual-MCP conflicts before changing them; do not register both.

For older clients without plugin support, use an explicitly supported upstream manual MCP path. Inspect `codex mcp add --help` and the package entry point before merging necessary configuration. Configure hooks only when supported. If only MCP tools can be provided, state “MCP only; automatic routing unverified/unavailable” and let the user decide whether that limitation is acceptable.

**Claude Code:** inspect current CLI plugin installation help and use the upstream `mksglu/context-mode` marketplace route. Perform and verify it when the host can operate that client. An upstream MCP-only alternative must be labelled as lacking plugin hooks/commands. Do not install Claude Code merely to add context-mode when the user did not select that client.

**Other clients:** read only the selected client's upstream instructions. If no verifiable install route exists, identify that limitation instead of reusing Codex configuration as a universal format.

For every route, check the runtime and PATH visible to the client subprocess. Do not copy an upstream `AGENTS.md` over existing project rules; inspect and merge needed routing guidance. Explain global scope before installation because it can affect other projects.

## Verify and record each layer

| Layer | Required evidence |
| --- | --- |
| Installed | Located package/plugin, version or commit, and runtime prerequisites |
| Registered | Correct entry in the target client, parseable config, no duplicate registration |
| Usable in this session | Discovered tools with results from `ctx_doctor` and `ctx_stats`, or precise failures |
| Routing/hooks | Supported, enabled, and trusted in this client, plus an actual harmless test or event evidence; stats alone is insufficient |

Follow host-exposed tool schemas. A small synthetic `ctx_execute` sample can verify tool output without reading user data. Test hooks only with an upstream-defined harmless matching case. A hook file alone warrants “configured, runtime unverified.”
Where record writing is already authorized and its location established, save install method, version, scope, backup path, tool checks, hook status, and remaining steps locally. For check-only requests without writing authorization or an established path, report in the conversation without creating files. Do not store credentials or upload entire diagnostics.

For “already installed, check only,” begin with read-only checks; explain any proposed repair and obtain authorization before reinstalling/upgrading. Keep installation preference separate from runtime requirements: unavailable required capabilities block affected tasks, while optional ones follow agreed fallback. Clearly distinguish installed from integration verified.
