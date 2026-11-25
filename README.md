# Lean Trace

Lean Trace helps coding agents investigate bugs, make focused changes, and explain the root cause with evidence. It uses targeted reads and concise test output. For longer tasks, it carries forward the active repository, constraints, decisions, verification, and open work.

## How it can reduce token use

- **Read less per task.** Start with symbol searches, relevant callers, and short file excerpts. Expand the search when the evidence points to another layer.
- **Keep tool output focused.** Return the exit status, failed cases, and nearby diagnostics. Keep full logs available locally for follow-up.
- **Use one agent by default.** Delegate a separate investigation or review when it is likely to prevent rework or catch a consequential regression. Each subagent consumes its own tokens.
- **Reduce repeated work.** Carry forward the active repository and revision, constraints, decisions, checks, and open work so a resumed session can pick up from verified facts.

These practices can reduce model input and avoid unnecessary calls. Credit use depends on how your host meters model usage, cache hits, tool calls, and retries. Use the host's usage and billing records to see what a task actually consumed.

## How it works in your environment

Lean Trace runs as instructions inside your coding agent. It uses the shell, tools, permissions, and project instructions that the host makes available. It does not require a proxy or background service.

At the start of a task, the agent identifies the active repository and the scope of the change. It checks the starting diff, preserves unrelated edits, and uses the repository's existing commands to reproduce and verify the change. If a tool, dependency, or permission is unavailable, the handoff states which check could not run.

Before switching repositories or handing off, the agent records a short checkpoint. On resume it rechecks the repository, diff, and facts that may have changed. Access to files, network services, and model processing follows your host's settings.

## Fork and clone

Select **Fork** on GitHub. Replace `YOUR-GITHUB-USERNAME` with your account name, then clone your fork:

```sh
git clone https://github.com/YOUR-GITHUB-USERNAME/lean-trace.git
cd lean-trace
```

## Install

**Codex:** From the cloned repository, run:

```sh
mkdir -p "$HOME/.codex/skills/lean-trace"
cp SKILL.md "$HOME/.codex/skills/lean-trace/"
cp -R subagents "$HOME/.codex/skills/lean-trace/"
```

If you use a custom Codex home, use its `skills` directory. Start a new session and invoke `$lean-trace`.

**Cursor:** Copy `.cursor/rules/lean-trace.mdc` into your project's `.cursor/rules/` directory. Cursor loads the rule in that project.

## Optional subagents

- [Trace Mapper](subagents/trace-mapper.md) traces an unfamiliar failure path and returns relevant code locations, evidence, and open questions.
- [Patch Verifier](subagents/patch-verifier.md) independently checks a consequential fix for correctness and regressions.

Lean Trace starts with one agent. The profiles travel with the skill and can be used as delegation instructions when the host supports subagents.
