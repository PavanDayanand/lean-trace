# Evaluation notes

## SpendyIOS backup import

The test used synthetic data against the legacy importer from commit `4636be5`. The Swift harness ran the extracted import method and real data models, with a save counter and substitutes for platform services. The iOS app and simulator were outside the test.

The original importer passed **6/11** checks. The proposed one-file patch passed **11/11**. The five failures involved incomplete category rows, mixed valid and invalid category rows, a category list of the wrong type, a subscriptions section of the wrong type, and a malformed 10,000-transfer backup. Valid data, transfer account references, and compatibility with an omitted optional subscriptions section were covered. Earlier setup consulted other skills. The fix and verification continued with Lean Trace’s instructions alone.

## Measure cost and continuity

1. Run matched tasks with and without Lean Trace. Use fresh sessions with the same model, effort settings, starting revision, permissions, and acceptance checks.
2. Score each result for correctness, scope, root-cause accuracy, and verification before looking at usage.
3. Collect total input, cached input, output, available credit records, and elapsed time. Include all retries and delegated calls.
4. On a longer ticket, force a resume and verify the active repository and revision, constraints, evidence-backed decisions, checks, and outstanding work.
5. Compare total credits per accepted fix across several matched tasks. When billing data is unavailable, report the token counts separately and leave credits unmeasured.
