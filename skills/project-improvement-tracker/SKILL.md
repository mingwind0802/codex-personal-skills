---
name: project-improvement-tracker
description: Maintain improvement records for material implementation changes, formal benchmarks, or explicit tracking requests. Respect project-local formats. Ordinary questions, status checks, read-only reviews, and standalone prose edits do not trigger record writes.
---

# Project Improvement Tracker

Keep a two-level project history: Detail is the auditable source of truth; Timeline is the compact daily view.

## Workflow

1. Read the applicable `AGENTS.md` and obey project-local names, schemas, and exclusions.
2. Determine whether the task calls for record updates. Reading this skill or reviewing project history does not itself authorize writes. Locate the two records in the target repository; create missing files only when an update is warranted.
3. Read Timeline first (search relevant rows in large files), then locate and read the matching Detail entry and local format rules. Do not read both histories in full by default. Reuse an existing ID for the same objective; otherwise check IDs in both files and assign the next `IMP-YYYYMMDD-NN` for that date.
4. Collect evidence from the implementation and tests. Record only observed values as facts.
5. Update Detail first using the project's record mode below.
6. Update the matching Timeline row with the latest status, 1–3 decisive metric changes, and the next action.
7. Verify both files use the same ID and do not claim improvement without comparable baseline and candidate measurements.

Update records in the same task that materially changes the project or its measured outcome. Do not wait for a separate documentation request.

## Detail Schema

Keep ID, date, title, status, objective, changed scope, validation evidence, and conclusion for each improvement. Add only fields relevant to the change:

- ID, date, title, status, objective, and changed scope;
- implementation summary and important design decisions;
- environment, model/dependency versions, dataset or load, and key configuration;
- for measured comparisons, a table with `指标 | 基线 | 改进后 | 变化 | 结论`; configuration fixes and architecture changes do not require artificial metric tables;
- test commands and artifact paths;
- conclusion, risks, rollback state, and next actions.

Use statuses: `规划中`, `进行中`, `待验证`, `已验证`, `失败`, `已回退` unless the project defines alternatives.

Record modes:

- Default audit mode: append dated/numbered rounds under the same ID; preserve failed and superseded measurements with their context.
- Project compact mode: when local AGENTS.md requires a final summary, update that summary and link original artifacts. Keep failures concise as required locally; do not delete original evidence or recreate per-round tables against local rules.

Local schemas and exclusions take precedence over this default template. Do not reorganize unrelated history as part of an update.

## Timeline Schema

Maintain one row per improvement:

```markdown
| 日期 | 改进 ID | 改进内容 | 状态 | 关键指标变化 | 下一步 |
```

Keep the row short. Put commands, complete tables, diagnostics, and explanations in Detail. Update an existing row rather than creating duplicate rows for the same ID.

## Metric Integrity

- Write `未测` when no measurement exists.
- Write `待补基线` when the candidate was measured without a comparable baseline.
- Write `不可比较` when conditions differ or a delta cannot be calculated responsibly.
- Calculate absolute delta as `candidate - baseline` and label units.
- Calculate percentage change only when the denominator and direction are meaningful; state whether lower or higher is better.
- Record workload, concurrency, warmup, precision, hardware, model, dependencies, and dataset whenever they can change results.
- Do not turn estimates, code inspection, one-off smoke checks, or theoretical capacity into verified gains.
- Record regressions, failures, and rollbacks so future work does not repeat them.

## Scope

Record changes that affect behavior or measurable project outcomes, including performance, quality, stability, resources, architecture, scheduling, and operational capacity. Skip standalone formatting, comments, or prose edits unless they are part of an existing tracked improvement.

For a formal benchmark within the authorized task, record measured results under the applicable ID, or create a benchmark entry. Ordinary investigations, explanations, status checks, and read-only reviews return findings without creating or updating records unless the user explicitly requests tracking. Explicit planning/tracking requests may create entries without an implementation.
