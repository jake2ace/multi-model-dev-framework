# Start a project with the skill

[简体中文](skill.md) | [Back to README](../README.en.md)

`multi-model-dev` turns project kickoff into a conversation. Describe your goal; it helps gather context, agree on assignments and budget, generate local inputs, and prepare the first task's handoff prompts. You do not need to manually copy and complete every template.

**This is a kickoff skill, not an automatic scheduler.** Execution and independent review still require manual arrangement in your existing tools. Model invocation, counters, the 25-minute timeout, and board updates are not automated.

## Install in Codex

The package is at [skills/multi-model-dev](../skills/multi-model-dev/SKILL.md). It includes bilingual workflows, templates, and the license, and can be copied independently without relying on an absolute framework checkout path.

Run from this repository on macOS / Linux:

```sh
skill_root="${CODEX_HOME:-$HOME/.codex}/skills"
mkdir -p "$skill_root"
if [ -e "$skill_root/multi-model-dev" ]; then
  echo 'Skill already exists; compare before updating. Nothing overwritten.'
else
  cp -R skills/multi-model-dev "$skill_root/multi-model-dev"
fi
```

Open a new Codex session and look for `multi-model-dev` in the skill list or enter `$multi-model-dev`. If it is not discovered, restart Codex and check again. A successful file copy does not verify loading in the current session.
You can also explicitly give the installed `SKILL.md` path to the agent. That tests manual loading, not automatic discovery.

Copying the skill only installs guidance files. During kickoff it explains context-mode benefits/tradeoffs and offers installation, skipping, or checking an existing setup. After opt-in the AI performs installation and verification, explicitly reporting required restarts or trust actions. It does not install Claude/models or change account permissions by default. Discovery and installation in other clients require separate verification; Claude Code compatibility has not been tested here.

## First invocation

Open Codex in the directory intended for your new project and send:

```text
$multi-model-dev
I want to build a new project: <one-sentence goal>.
Models I can use: <available models>.
Use English. Help me agree on the first version, roles, and budget.
Ask about missing key decisions and prepare the first task after
the configuration is confirmed.
```

You can begin discussing without a directory or chosen stack. The skill establishes a target path before writing. Do not assume a framework-development chat should create your new application inside the framework repository.

It should reuse supplied facts, ask a few important questions, and present a concrete proposal. Roles are not fixed models; you choose the coordinator too. There is no need to enable every provider just to fill the profile.

## context-mode is your choice

- **Potential benefit:** retrieve relevant results from large files, logs, and batch searches to reduce raw context input.
- **Tradeoffs:** dependencies, maintenance, possible latency, and local storage for indexes/session records. Small tasks may not benefit; subscription savings are not guaranteed.
- **Options:** install and verify / skip for now / already installed, check only. Skipping does not prevent basic use.

After opt-in, the skill checks the client and current official method, inspects existing installations, backs up relevant config, installs/registers, and verifies tools and hooks. Required restarts or trust actions stay pending for continuation; installed files are not proof of a working integration. Setup requires the host's tools and permissions; it is not a standalone cross-platform installer.

## Expected results

1. **Kickoff proposal:** first-version goal and acceptance, models/effort, estimated calls, and stopping conditions.
2. **Two local files:** `PROJECT_CONTEXT.md` and `WORKFLOW_PROFILE.md`; unconfirmed configurations stay draft.
3. **Next action:** after configuration confirmation and a request to trial the task, a task file and executor/reviewer prompts. Unrun work stays marked unrun.

The suggested record location is `.multi-model-dev/<project-id>/` within the target project, or a location you specify. The skill preserves existing content and checks Git ignore behavior. Keep real context, records, and credentials out of public commits. The installed package holds generic guidance, not your project inputs.

## Test this version

Start by checking the kickoff experience:

- Does it repeat questions you already answered?
- Can it give a clear recommendation when the stack is uncertain?
- Does it silently choose models, mark a profile confirmed, or start changing application code?
- Are the two files accurate, and are existing files preserved?
- Is it clear who acts next, how to verify the result, and when to stop?

Structural validation and installed-file comparisons establish package integrity only. Automatic discovery, real conversational behavior, and savings need actual session testing. After the first task, use the [comparison guide](quickstart.en.md#how-to-check-whether-it-saves-usage-and-time) to record quality, time, and consumption.

## Updates and maintenance

Repository updates do not automatically replace the local installation. Compare local edits before copying a selected version. Keep project inputs outside the skill package.
When changing `templates/`, maintain matching distribution copies in `skills/multi-model-dev/assets/`. Keep the bundled LICENSE identical to the repository license. Installing the skill does not alter the license terms.

References: [OpenAI skill structure](https://developers.openai.com/plugins/build/skills), [local skills and evaluation examples](https://developers.openai.com/blog/eval-skills).
