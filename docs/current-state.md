# Current State Snapshot

This file records the current Codex-visible skills and the current Claude plugin install state for this workspace.

Captured from:

- `~/.codex/skills`
- `~/.codex/superpowers`
- `~/.codex/pua`
- `~/.claude/plugins/installed_plugins.json`

## Codex-Visible Skills

There are 38 `SKILL.md` folders visible in the current Codex install.

### Built-in Codex System Skills

These 5 skills are present in Codex, but they are not installed from `skills.manifest.json`:

- `imagegen`
- `openai-docs`
- `plugin-creator`
- `skill-creator`
- `skill-installer`

`skill-creator` also exists in the repository-managed skill tree, so it appears in both the built-in and tracked inventories.

### Repository-Managed Skills

These 33 skills are tracked by `codex_skills_pack` and bootstrap can install them directly:

- `web-access`
- `brainstorming`
- `dispatching-parallel-agents`
- `executing-plans`
- `finishing-a-development-branch`
- `receiving-code-review`
- `requesting-code-review`
- `subagent-driven-development`
- `systematic-debugging`
- `test-driven-development`
- `using-git-worktrees`
- `using-superpowers`
- `verification-before-completion`
- `writing-plans`
- `writing-skills`
- `frontend-design`
- `algorithmic-art`
- `brand-guidelines`
- `canvas-design`
- `claude-api`
- `doc-coauthoring`
- `docx`
- `internal-comms`
- `mcp-builder`
- `pdf`
- `pptx`
- `skill-creator`
- `slack-gif-creator`
- `theme-factory`
- `web-artifacts-builder`
- `webapp-testing`
- `xlsx`
- `patch-context-hygiene`

## Current Claude Plugin Install State

The following plugins are installed in Claude. They are documented here because Codex uses their skill content, but Claude plugin wrappers themselves are not installed into Codex.

| Plugin | Source repo | Version | Install path | Notes |
|---|---|---|---|---|
| `superpowers@claude-plugins-official` | `https://github.com/obra/superpowers.git` | `5.0.6` | `C:\Users\ChenZiLiang\.claude\plugins\cache\claude-plugins-official\superpowers\5.0.6` | Provides the 14 Superpowers workflow skills. |
| `frontend-design@claude-plugins-official` | `https://github.com/anthropics/claude-plugins-official.git` | `unknown` | `C:\Users\ChenZiLiang\.claude\plugins\cache\claude-plugins-official\frontend-design\unknown` | Provides the canonical `frontend-design` skill. |
| `document-skills@anthropic-agent-skills` | `https://github.com/anthropics/skills.git` | `98669c11ca63` | `C:\Users\ChenZiLiang\.claude\plugins\cache\anthropic-agent-skills\document-skills\98669c11ca63` | Provides the 16 document and technical skills from `anthropic/skills`. |
| `pua@pua-skills` | `https://github.com/tanweai/pua.git` | `3.1.0` | `C:\Users\ChenZiLiang\.claude\plugins\cache\pua-skills\pua\3.1.0` | Provides the PUA plugin bundle and its own skill set. |

## Local Plugin Source Checkouts

The Codex workspace also has local plugin source checkouts under `~/.codex`:

- `~/.codex/superpowers`
  - Skills: `brainstorming`, `dispatching-parallel-agents`, `executing-plans`, `finishing-a-development-branch`, `receiving-code-review`, `requesting-code-review`, `subagent-driven-development`, `systematic-debugging`, `test-driven-development`, `using-git-worktrees`, `using-superpowers`, `verification-before-completion`, `writing-plans`, `writing-skills`
- `~/.codex/pua`
  - Skills: `mama`, `p10`, `p7`, `p9`, `pro`, `pua`, `pua-en`, `pua-ja`, `pua-loop`, `shot`, `yes`

These source checkouts are separate from the installable Codex skill tree under `~/.codex/skills`.
