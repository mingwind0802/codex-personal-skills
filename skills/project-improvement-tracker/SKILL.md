---
name: project-improvement-tracker
description: Track material project improvements and experiments with linked, reproducible decisions while keeping current records compact.
---

# Project Improvement Tracker

Keep project history useful without letting the default agent read set grow with time.

## Structure

Use three levels:

1. **Timeline** — compact index.
2. **Detail** — one bounded record per `IMP-YYYYMMDD-NN`.
3. **Artifact** — existing code, patches, configs, logs, benchmark outputs, reports, and retained results.

Artifacts are evidence and recoverable implementations. Detail records decisions. Timeline indexes Detail. Do not create a separate Evidence log or duplicate evidence documents.

## Workflow

1. Read applicable `AGENTS.md` and `WORKSPACE.md`.
2. Read current Timeline.
3. Follow the IMP link and read only the relevant Detail.
4. Read artifacts only when verification or debugging requires them.
5. Reuse the same IMP for the same objective. Create a new IMP only when the objective or phase materially changes; length alone is not a reason.
6. After a material experiment or change, update Detail, then Timeline.

Do not scan all Details or archives by default. Use the record and artifact locations established in `WORKSPACE.md` when present.

## Status and Timeline

Use statuses: `进行中`, `暂停`, `已完成`, `已放弃`.

Use:

```markdown
| 日期 | 改进 ID | 改进内容 | 状态 | 关键结果 | 下一步 |
|---|---|---|---|---|---|
| YYYY-MM-DD | [IMP-YYYYMMDD-NN](relative/path/to/detail.md) | ... | 进行中 | ... | ... |
```

The IMP ID must link directly to its Detail using a path relative to the Timeline document. Keep one short row per IMP.

Current Timeline contains all `进行中` IMPs and the latest roughly 30 non-active records. Move older `暂停`, `已完成`, and `已放弃` rows to date-based archives; when work resumes, move its row back. Never renumber an IMP or its EXP entries during compaction, archival, or restoration.

## Detail

Detail should answer:

**做了什么 → 指标怎么变 → 为什么采用或放弃 → 实现和证据在哪里 → 下一步是什么**

```markdown
# IMP-YYYYMMDD-NN 标题

状态：
目标：
涉及仓库：
前置／后继：仅有依赖或阶段承接时填写

## 当前结论

- 当前采用：EXP-xx，采用原因。
- 关键结果：相对基线的主要收益与代价。
- 尚未确认：仅填写影响判断的未验证事项。

## 下一步

下一项明确的实验或动作；已结束则写“无”。

## 比较口径

基线、评估数据／版本、关键评估条件。
共同条件只写一次，后续实验仅说明差异。

## 实验记录

| 实验 | 方法／关键改动 | 结果与代价 | 决策／原因 | 实现与证据 |
|---|---|---|---|---|
| EXP-01 | 改了什么、关键设置 | 基线→结果及变化 | 采用／不采用／待验证及原因 | 代码、配置、结果链接 |

## 保留成果

仅列当前采用、历史最优或指定回退版本的产物入口。
没有则省略。
```

“方法／关键改动”必须具体到足以区分实验，例如“增加一层通道混合，通道数 32→64”，不能只写“优化模型结构”。分别判断“当前采用”和“指标最好”：效果最好但资源、稳定性或其他约束不合格的实验可以不采用，并记录原因。

非指标型改进使用“原行为→验证后的行为”记录，不强行填写数值。

## Traceability

对决策有影响的实验，关联对应代码版本、实际配置和结果证据。跨仓库实验在“涉及仓库”和实验记录中标明各实现位置。

存在未提交改动时，保留能够识别或恢复该实验实现的补丁或快照，不能仅引用提交号。不要求为每次小改动复制整个仓库，也不增加哈希校验流程。优先复用已有运行记录，不重复生成证据文档。

## Failed or Incomplete Experiments

保持简短并区分：

```text
无收益：尝试了什么；有效评估结果；本次不采用的原因。
未完成：尝试了什么；失败环节；尚不能判断方法效果；下一步。
```

只有证据支持时，才写“后续避免重复路线”。

## Compaction and Retention

Detail is curated decision history, not an append-only audit log. If a Detail exceeds roughly 10–15 meaningful experiments or 80 lines, organize it: first merge repeated debugging and rounds that do not affect decisions.

Never compact away a historical best, key negative conclusion, reason for replacing a solution, or rollback entry. If the record remains too long, move the complete old record into an on-demand archive and retain its summary and link in current Detail. Compaction does not authorize deleting artifacts.

Create a successor IMP only when the phase or objective truly changes. Handle growth in the same phase through archival. EXP numbering within an IMP remains monotonic and is never reset by organization or archival.

## Metric Integrity

Use comparable baseline and candidate conditions. Use `未测`, `待补基线`, or `不可比较` when appropriate.

Do not report estimates, code inspection, theoretical capacity, or smoke tests as verified gains. If records conflict, verify the underlying Artifact, then correct Detail and Timeline.

Protecting historical versions can increase disk use. Control temporary artifact accumulation and default reading scope; do not delete important historical implementations merely to hold total storage constant.
