# Codex Personal Skills

Private collection of reusable Codex skills.

## Skills

- `agents-init`: Investigates a project and establishes durable rules, locations, `AGENTS.md`, `WORKSPACE.md`, and CodeGraph entry points. Explicit invocation only.
- `project-improvement-tracker`: Tracks reproducible project improvements through a linked Timeline, Detail records, and existing artifacts.
- `workspace-manager`: Maintains workspace navigation plus artifact placement, retention, and authorized temporary-file cleanup rules.

## Install on another device

```bash
python ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo mingwind0802/codex-personal-skills \
  --path \
    skills/agents-init \
    skills/project-improvement-tracker \
    skills/workspace-manager
```

The target device must have permission to read this private repository.
