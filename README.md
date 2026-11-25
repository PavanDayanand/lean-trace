# Lean Trace

Lean Trace helps coding agents investigate bugs, make focused changes, and explain the root cause with evidence. It uses targeted reads and concise test output. For longer tasks, it carries forward the active repository, constraints, decisions, verification, and open work.

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
