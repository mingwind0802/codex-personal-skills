# Codex Personal Skills

Private collection of reusable Codex skills.

## Skills

- `agents-init`: Investigates a project and initializes durable `AGENTS.md`, `WORKSPACE.md`, and CodeGraph entry points. Explicit invocation only.
- `project-improvement-tracker`: Tracks material project improvements using compact Timeline, Detail, and Artifact layers.
- `workspace-manager`: Maintains a compact `WORKSPACE.md` map when repository boundaries, responsibilities, dependencies, or important resource locations change.

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
