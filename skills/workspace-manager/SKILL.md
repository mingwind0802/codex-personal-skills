---
name: workspace-manager
description: Maintain WORKSPACE.md structure and artifact rules for complex projects. Use when repositories, responsibilities, dependencies, or important locations change, or when the user asks to organize the workspace, define artifact conventions, or clean temporary files.
---

# Workspace Manager

Maintain `WORKSPACE.md` as the compact navigation, placement, and retention map of the project.

It should answer:

**有什么 → 各自做什么 → 怎么关联 → 东西在哪里 → 如何归置和保留**

## Read and Scope

Read applicable `AGENTS.md` and `WORKSPACE.md` first. Only inspect affected repositories, directories, records, and references when verifying changes; do not rescan the whole project by default.

Use this skill when:

* repositories or major subprojects are added, removed, or replaced;
* responsibilities, fixed aliases, cross-repository dependencies, or key entry points change;
* important model, data, experiment-record, output, or shared-resource locations change;
* the existing map is materially inaccurate;
* the user asks to organize the workspace, establish artifact placement/retention conventions, or clean temporary files.

Ordinary code edits, single experiments, and temporary file creation do not require rerunning this skill. Follow established `WORKSPACE.md` rules directly.

## WORKSPACE Format

Use only applicable sections and rows:

```markdown
# Workspace

## 项目概述
一句话说明目标，并明确工作区根目录。

## 项目地图

| 固定简称 | 路径 | 类型 | 作用 | 来源 | 修改策略 | 关键入口 |
|---|---|---|---|---|---|---|
| ... | ... | 主项目／辅助／参考 | ... | 自研／GitHub | 可修改／原则上不改 | ... |

## 主要关系

- A → B：依赖、接口或数据流。

## 重要位置

| 内容 | 实际位置 | 归置／保留规则 |
|---|---|---|
| 改进记录 | 现有记录目录 | 跨仓库改进只维护一份主记录 |
| 实验结果 | 现有输出目录 | 用 IMP／EXP 关联，优先复用已有运行目录 |
| 临时试听／预览 | 实际临时目录 | 符合清理条件后可删除 |
| 保留版本 | 实际保存位置 | 当前采用、历史最优、指定回退版本受保护 |
| 共享数据／模型 | 实际位置 | 不因单次实验结束而删除 |
```

Do not list a complete file tree. Categories are logical rules and do not require creating matching directories. Record actual applicable locations only. Paths in WORKSPACE are relative to the workspace root; Markdown links are relative to the document containing them.

## File Placement

* Put code in the repository responsible for the feature and preserve its internal structure.
* Prefer existing output directories. If a run ID already exists, link it instead of adding directory layers.
* Name files by purpose and include IMP/EXP when useful; avoid names such as `final`, `new`, or `latest2` accumulating without meaning.
* Before creating a long-lived directory, verify that no existing location fits. If a new location is necessary, update the map.
* When moving files, update affected paths and Markdown links.
* Do not restructure third-party repositories for uniformity.

## Artifact Retention

| Type | Default handling |
|---|---|
| Current adopted, historical best, or designated rollback version | Retain; delete only when the user explicitly requests it |
| Configs, compact evaluation results, and necessary implementation records supporting conclusions | Retain with the conclusion |
| Listening samples, preview images, caches, and debug dumps | Clean according to temporary-artifact rules |
| Unknown purpose or dependency | Do not delete until resolved |

Listening samples are temporary by default. Reclassify them as retained results when they become important subjective-evaluation evidence or the user requests retention.

Protecting historical versions can increase disk use. Control temporary artifact accumulation and default reading scope; do not delete important historical implementations merely to hold total storage constant.

## Cleanup Safety

Deleting files requires all of these conditions:

1. the target is inside an agreed temporary scope;
2. its purpose has ended;
3. no running task or retained result depends on it;
4. deletion is covered by the user's existing cleanup authorization.

Invocation of this skill or a general organization request does not by itself expand deletion authority. Do not infer safety from extension, age, or the fact that a file was superseded. If purpose or dependencies are unclear, do not delete it.

After authorized cleanup, report categories, counts, and freed space; do not create a permanent record for every temporary file. If an experiment record links to a removed sample, mark it briefly as “临时样本已清理” while preserving necessary results and conclusions.

## Keep It Compact

WORKSPACE describes stable boundaries, entry points, locations, placement, and retention rules. Keep implementation details in the relevant repository and experiment decisions in tracker records. If WORKSPACE grows, retain navigation and move detail back to its owning documentation.

**WORKSPACE 负责告诉你去哪里找、如何归置和保留，而不是解释所有东西怎么实现。**
