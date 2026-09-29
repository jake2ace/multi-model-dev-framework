# context-mode: updates and MCP usage

[简体中文](context-mode.md) | [Home](../README.en.md)

## Upstream update links

- [Official repository and instructions](https://github.com/mksglu/context-mode)
- [Latest published release: redirects to upstream's latest release](https://github.com/mksglu/context-mode/releases/latest)
- [All releases and release notes](https://github.com/mksglu/context-mode/releases)
- [Commits on main](https://github.com/mksglu/context-mode/commits/main/)

These links show upstream content when opened. This repository neither vendors upstream code nor presents a cached version number as live status. Commits on main may be unreleased. A new upstream release does not establish the installed version or authorize an upgrade.

## MCP tools for smaller context inputs

[context-mode](https://github.com/mksglu/context-mode) processes large outputs outside the model context, indexes content, and retrieves relevant passages. When integrated and used appropriately, this can reduce context input and some token consumption. No specific subscription allowance or cost reduction is guaranteed.

| Use | MCP tool |
| --- | --- |
| Execute and return relevant results | `ctx_execute` |
| Process file content | `ctx_execute_file` |
| Run batches and retrieve results | `ctx_batch_execute` |
| Index and retrieve information | `ctx_index` → `ctx_search` |
| Fetch and index web content | `ctx_fetch_and_index` → `ctx_search` |
| Inspect session usage statistics | `ctx_stats` |
| Diagnose installation and integration | `ctx_doctor` |

Platform prefixes vary. Discover actual tools and input schemas in the running session rather than hardcoding a universal name. See the [upstream MCP implementation](https://github.com/mksglu/context-mode/blob/main/src/server.ts).

## Suggested workflow

1. Before project execution, agree whether context-mode is required or optional in the workflow profile.
2. Follow upstream instructions for the selected client. Discover tools, then call `ctx_doctor` and `ctx_stats`. Successful statistics retrieval does not prove routing hooks are active.
3. Route large logs, batch searches, and file analysis through appropriate tools; return enough evidence to make the decision. Avoid extra calls for tiny inputs.
4. After real work, inspect statistics again in the same session. Preserve complete diagnostic evidence; never discard failures merely to shorten context.
5. Report unavailability explicitly. Pause affected tasks when required, or follow the agreed fallback when optional. Installed does not mean in use.

These are usage conventions, not an implemented router or telemetry collector.

## Statistics are not allowance accounting

Context measurements and upstream token or dollar estimates are not Codex weekly allowance accounting. Record source, session, units, baseline, and estimation method; leave unknowns unknown. Upstream includes estimation conversions: see the [statistics implementation](https://github.com/mksglu/context-mode/blob/main/src/server.ts). This framework has no measured allowance-saving benchmark.

## Update boundaries

Use the upstream links to inspect changes. This repository has no background poller, automatic notifications, automatic upgrades, or live status dashboard. Compare the installed version with the target release and read compatibility notes before upgrading; verify tools and hooks afterwards. Checking updates does not authorize `ctx_upgrade`.

context-mode is an independent project governed by [its own license](https://github.com/mksglu/context-mode/blob/main/LICENSE).
