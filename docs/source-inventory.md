# Source Inventory

This repository defines the installable skill inventory consumed by the WSL bootstrap repository, including upstream skills and skills you maintain locally. Codex also ships 5 built-in system skills that are visible in the current install but are not sourced from this manifest.

## Canonical Sources

| Source | Purpose | Installed skills |
|---|---|---|
| `eze-is/web-access` | Local web automation and browser/CDP guidance | `web-access` |
| `obra/superpowers` | The 14 Superpowers workflow skills | `brainstorming`, `dispatching-parallel-agents`, `executing-plans`, `finishing-a-development-branch`, `receiving-code-review`, `requesting-code-review`, `subagent-driven-development`, `systematic-debugging`, `test-driven-development`, `using-git-worktrees`, `using-superpowers`, `verification-before-completion`, `writing-plans`, `writing-skills` |
| `anthropics/claude-plugins-official` | The canonical `frontend-design` skill | `frontend-design` |
| `anthropics/skills` | Document and technical helper skills | `algorithmic-art`, `brand-guidelines`, `canvas-design`, `claude-api`, `doc-coauthoring`, `docx`, `internal-comms`, `mcp-builder`, `pdf`, `pptx`, `skill-creator`, `slack-gif-creator`, `theme-factory`, `web-artifacts-builder`, `webapp-testing`, `xlsx` |
| `codex-skills-pack` | Locally maintained helper skills for this repository | `patch-context-hygiene` |

## Built-in Codex System Skills

These skills are present in the current Codex install, but they are not installed from `skills.manifest.json`:

- `imagegen`
- `openai-docs`
- `plugin-creator`
- `skill-creator`
- `skill-installer`

## Local Skills

This pack is also the home for your personal skills. Add new locally authored skills here, then register them in `skills.manifest.json` so bootstrap can install them alongside upstream sources.

## Conflict Rule

`frontend-design` exists in both `anthropics/claude-plugins-official` and `anthropics/skills`.

This repository intentionally installs the version from `anthropics/claude-plugins-official` because it matches the currently installed Claude plugin source. The `anthropics/skills` copy is excluded.

## What Gets Installed

Only `SKILL.md`-style skill folders are copied into Codex.

Plugin wrapper metadata, marketplace state, and Claude-specific settings do not transfer directly. They are documented here so the bootstrapper can reproduce the useful skill content rather than the plugin container.
