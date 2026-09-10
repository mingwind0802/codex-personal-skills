---
name: project-improvement-tracker
description: Track material project improvements and experiments.
---

# Project Improvement Tracker

Keep project history useful without letting the default agent read set grow with time.

## Structure

Use three levels:

1. **Timeline** — compact index.
2. **Detail** — one bounded record per `IMP-YYYYMMDD-NN`.
3. **Artifact** — existing logs, configs, benchmark outputs, reports, etc.

Artifacts are raw evidence. Detail records decisions. Timeline indexes Detail.

Do not create a separate Evidence log.

## Workflow

1. Read applicable `AGENTS.md`.
2. Read current Timeline.
3. Read only the relevant Detail.
4. Read artifacts only when verification or debugging requires them.
5. Reuse the same IMP for the same objective; create a new IMP when the objective or phase materially changes.
6. After a material experiment or change, update Detail, then Timeline.

Do not scan all Details or archives by default.

## Timeline

Use:

```markdown
| 日期 | 改进 ID | 改进内容 | 状态 | 关键结果 | 下一步 |
```

Keep one short row per IMP.

Current Timeline contains all active IMPs and only the latest ~30 closed IMPs. Move older closed rows to date-based archives and search archives only when needed.

## Detail

Detail should answer:

**做了什么 → 指标怎么变 → 得出什么结论 → 下一步是什么**

```markdown
# IMP-... 标题

状态：
目标：
前置：
后继：

## 当前结论
当前采用方案及最重要的 1–3 个结果。

## 下一步
下一项实验或动作。

## 实验记录

| 实验 | 核心改动 | 关键指标变化 | 结论 |
|---|---|---|---|
| EXP-01 | ... | PESQ 2.31→2.39 (+0.08) | 保留 |

## Artifact
- path/to/result
```

Only record decision-relevant experiments and 1–3 important metrics.

Failed experiments normally use one sentence:

```markdown
- 失败：<尝试>；<结果>；<判断>；后续避免 <重复路线>。
```

Do not copy full logs, commands, debugging history, or large result tables.

Detail is curated decision history, not an append-only audit log. Collapse minor superseded rounds.

If a Detail exceeds roughly 10–15 meaningful experiments or ~80 lines, compact it. If the work has entered a new phase or question, close it and create a successor IMP.

## Metric Integrity

Use comparable baseline and candidate conditions.

Use `未测`, `待补基线`, or `不可比较` when appropriate.

Do not report estimates, code inspection, theoretical capacity, or smoke tests as verified gains.

If records conflict, verify the underlying Artifact, then correct Detail and Timeline.
