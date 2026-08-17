---
name: project-improvement-tracker
description: Maintain concise project improvement history in a detailed record and a timeline summary. Use for project management work that plans, implements, validates, reviews, or summarizes improvements, TODOs, milestones, benchmarks, regressions, or changes to performance, concurrency, latency, accuracy, reliability, resources, architecture, and scheduling. Create or update IMPROVEMENT_DETAIL.md and IMPROVEMENT_TIMELINE.md, respecting project-local AGENTS.md overrides.
---

# Project Improvement Tracker

Keep a two-level project history: Detail is the auditable source of truth; Timeline is the compact daily view.

## Workflow

1. Read the applicable `AGENTS.md` and obey project-local names, schemas, and exclusions.
2. Locate `IMPROVEMENT_DETAIL.md` and `IMPROVEMENT_TIMELINE.md` from the repository root. If absent, create both using the schemas below.
3. Read both files before changing them. Reuse an existing improvement ID when continuing the same objective; otherwise assign `IMP-YYYYMMDD-NN` using the next sequence for that date.
4. Collect evidence from the implementation and tests. Record only observed values as facts.
5. Update Detail first. Append a new experiment round instead of replacing prior measurements.
6. Update the matching Timeline row with the latest status, 1–3 decisive metric changes, and the next action.
7. Verify both files use the same ID and do not claim improvement without comparable baseline and candidate measurements.

Update records in the same task that materially changes the project or its measured outcome. Do not wait for a separate documentation request.

## Detail Schema

For each improvement include:

- ID, date, title, status, objective, and changed scope;
- implementation summary and important design decisions;
- environment, model/dependency versions, dataset or load, and key configuration;
- a Markdown metric table with `指标 | 基线 | 改进后 | 变化 | 结论`;
- test commands and artifact paths;
- conclusion, risks, rollback state, and next actions.

Use statuses: `规划中`, `进行中`, `待验证`, `已验证`, `失败`, `已回退` unless the project defines alternatives.

For multiple experiments under one ID, append dated/numbered rounds. Preserve failed and superseded measurements with their context.

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

When a task only investigates or benchmarks without implementing a change, update an existing improvement when applicable; otherwise create an investigation entry if its result materially changes project decisions.
