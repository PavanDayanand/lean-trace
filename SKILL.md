---
name: lean-trace
description: Debug and change code with focused context, surgical diffs, and verified root-cause handoffs. Use when reducing coding-agent overhead while preserving correctness and continuity.
---

# Lean Trace

## Investigate

- Pin the active repo, symptom, expected behavior, and scope. Use symbol searches, relevant callers, and bounded reads. Expand when evidence points across a boundary or an invariant is unclear.
- For a bug, reproduce it where practical. Trace the input through the failing condition to the observed effect. Distinguish observed cause from hypothesis.
- Capture command status, failed cases, and nearby diagnostic lines. Preserve full logs locally when needed. Keep successful output to a summary and never mask a failure while filtering.
- Work directly by default. When the added cost is justified and the host permits delegation, use a [Trace Mapper](subagents/trace-mapper.md) to locate a failure across layers or a [Patch Verifier](subagents/patch-verifier.md) to independently check a consequential fix. Read only the selected profile. Give the role a narrow scope and ask for evidence and open questions.

## Change and verify

- Reuse the existing path. Change the smallest semantic unit that solves the cause. For a one-line fix, use a narrow hunk and preserve the surrounding block, comments, formatting, and unrelated user edits. Review the diff against the starting state. Explain any broader replacement.
- Keep existing behavior, validation, and meaningful tests. Re-run the reproducer, then check nearby edge cases and affected callers. Expand verification with the blast radius. Use approved tools and data boundaries.

## Carry context and report

- Before a handoff, context reset, or repo switch, retain a short checkpoint with repo and revision, goal and constraints, evidence-backed decisions, changed files, checks, and open work. On resume, verify the repo, diff, and any facts that may have changed. Save the checkpoint in the existing handoff channel when needed.
- State the symptom, the exact condition causing it and how it leads to the outcome, the change, and checks actually run. Call out material verification gaps. Keep the explanation proportionate to complexity. Record real debt in the team's existing tracker when needed.
- For a cost study, use host usage records when available. Compare matched runs and include cached input, output, retries, and delegated calls. Report billed credits only from billing data. Label byte counts as size measurements.
