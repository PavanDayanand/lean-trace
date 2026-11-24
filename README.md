# Lean Trace

Lean Trace helps coding agents investigate bugs, make focused changes, and explain the root cause with evidence. It uses scoped reads, concise test output, and one agent by default. For longer work, it carries forward the repository, constraints, decisions, verification, and open work.

## Optional subagents

- [Trace Mapper](subagents/trace-mapper.md) follows unfamiliar code paths and returns evidence, relevant locations, and open questions.
- [Patch Verifier](subagents/patch-verifier.md) independently checks a consequential change for correctness and regressions.

Lean Trace works in one session by default. Use either role when the task justifies another model call.

## Use it

- **Codex** — Copy this folder to your personal skills directory as `lean-trace`, then invoke `$lean-trace` in a new turn.
- **Cursor** — Copy `.cursor/rules/lean-trace.mdc` into the project’s `.cursor/rules/` directory to apply the rule throughout that project.

A bug-fix handoff should explain the symptom, the condition that caused it, how that condition led to the outcome, the change, and what passed.

## Evaluation

In an isolated SpendyIOS backup-import test, the original importer passed 6 of 11 checks. The proposed patch passed 11 of 11, including a valid 10,000-transfer import and rejection of a malformed backup without changing prior state or scheduling a save.

The test measured correctness. Billed credit savings and context retention after compaction are unmeasured. See the [benchmark notes](benchmarks/README.md) for scope and a cost-measurement protocol.
