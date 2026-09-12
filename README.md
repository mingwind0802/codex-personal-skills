# Codex Personal Skills

Private collection of reusable Codex skills.

## Skills

- `agents-init`: Investigates a project and establishes durable rules, locations, `AGENTS.md`, `WORKSPACE.md`, and CodeGraph entry points. Explicit invocation only.
- `project-improvement-tracker`: Tracks reproducible project improvements through a linked Timeline, Detail records, and existing artifacts.
- `workspace-manager`: Maintains workspace navigation plus artifact placement, retention, and authorized temporary-file cleanup rules.
- `weekly-report`: Summarizes weekly progress from Timeline and Detail as concise bullets, with useful comparison tables and one or two sentences each for issues and next week's plan.

## Weekly reports

Ask: `使用 $weekly-report 根据当前项目的 Timeline 和 Detail 写本周周报。`

The default report uses 200–400 Chinese characters of prose, plus useful tables, under three sections: 本周工作、难点与问题、下周计划. You can specify another date range or length. Source records are read only.

## Install on another device

```bash
python ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo mingwind0802/codex-personal-skills \
  --path \
    skills/agents-init \
    skills/project-improvement-tracker \
    skills/workspace-manager \
    skills/weekly-report
```

The target device must have permission to read this private repository.
