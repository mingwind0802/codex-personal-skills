---
name: workspace-manager
description: Maintain the WORKSPACE.md map for complex or multi-repository projects. Use when repositories, major directories, responsibilities, dependencies, or important resource locations change.
---

# Workspace Manager

Maintain `WORKSPACE.md` as the compact navigation map of the project.

It should answer:

**有什么 → 各自做什么 → 怎么关联 → 东西在哪里**

## Read

Read `WORKSPACE.md` first.

Only inspect affected repositories or directories when verifying changes. Do not rescan the whole project by default.

## Format

Prefer:

```markdown
# Workspace

## 项目概述
一句话说明整个 workspace 的目标。

## 项目地图

| 路径 | 类型 | 作用 | 来源 | 修改策略 |
|---|---|---|---|---|
| ... | 主项目 / 辅助 / 参考 | ... | 自研 / GitHub | 可修改 / 原则上不改 |

## 主要关系

- A → B：...
- B → C：...

## 重要位置

| 内容 | 位置 |
|---|---|
| 训练代码 | ... |
| 推理/部署 | ... |
| 模型 | ... |
| 实验记录 | ... |
| 临时产物 | ... |
| 保留成果 | ... |
```

只保留实际适用的部分。

## Update when

更新 WORKSPACE 当：

* 新增、删除或替换仓库/主要子项目；
* 仓库职责发生变化；
* 新增重要跨仓库依赖；
* 模型、数据、实验记录或共享资源的位置发生变化；
* 现有地图已经明显失真。

普通代码修改、单次实验和临时文件不触发更新。

## Rules

保持每个仓库原有内部结构。

不要为了统一格式重构第三方仓库。

WORKSPACE 只描述稳定边界和位置；详细实现留在对应 repo 的文档中。

如果内容越来越长，留下入口和路径，把细节移回对应 repo。

**WORKSPACE 负责告诉你去哪里找，而不是解释所有东西怎么实现。**
