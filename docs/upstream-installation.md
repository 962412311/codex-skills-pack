# Upstream Installation Notes

This file records the original install instructions or source location for each upstream skill source. The bootstrap repo should consume this manifest, not rediscover these instructions dynamically.

## Recovery Matrix

| Source | Upstream repo | Upstream install instruction | Codex recovery target |
|---|---|---|---|
| `web-access` | `https://github.com/eze-is/web-access.git` | Clone the repo and copy `SKILL.md` into `~/.claude/skills/web-access` | `~/.codex/skills/web-access` |
| `superpowers` | `https://github.com/obra/superpowers.git` | Follow `https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.codex/INSTALL.md` | `~/.codex/superpowers` + `~/.agents/skills/superpowers` |
| `frontend-design` | `https://github.com/anthropics/claude-plugins-official.git` | `/plugin install frontend-design@claude-plugins-official` | `plugins/frontend-design/skills/frontend-design` |
| `document-skills` | `https://github.com/anthropics/skills.git` | `/plugin marketplace add anthropics/skills` then `/plugin install document-skills@anthropic-agent-skills` | `skills/<skill-name>` for `document-skills`, `docx`, `pdf`, `pptx`, `xlsx` |
| `pua` | `https://github.com/tanweai/pua.git` | Follow `https://raw.githubusercontent.com/tanweai/pua/main/.codex/INSTALL.md` | `~/.codex/pua` + `~/.codex/skills/pua` + `~/.codex/prompts/pua.md` |

## Source Notes

### `web-access`

- Source repo: `https://github.com/eze-is/web-access.git`
- Original install method: clone the repository and copy `SKILL.md` into `~/.claude/skills/web-access`
- Direct reference: `git clone https://github.com/eze-is/web-access ~/.claude/skills/web-access`

### `superpowers`

- Source repo: `https://github.com/obra/superpowers.git`
- Original Codex install instruction from the upstream README:

```text
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.codex/INSTALL.md
```

### `frontend-design`

- Source repo: `https://github.com/anthropics/claude-plugins-official.git`
- Upstream Claude Code install instruction:

```text
/plugin install frontend-design@claude-plugins-official
```

- Codex extraction path: `plugins/frontend-design/skills/frontend-design`

### `anthropics/skills`

- Source repo: `https://github.com/anthropics/skills.git`
- Upstream Claude Code install instruction:

```text
/plugin marketplace add anthropics/skills
/plugin install document-skills@anthropic-agent-skills
```

- Codex extraction paths: `skills/<skill-name>`

### `pua`

- Source repo: `https://github.com/tanweai/pua.git`
- Original Codex install instruction from the upstream README:

```text
Follow the instructions in https://raw.githubusercontent.com/tanweai/pua/main/.codex/INSTALL.md
```

## Rule

When adding a new source, record:

1. The upstream repository URL
2. The upstream install command or source path
3. The Codex extraction path in `skills.manifest.json`
4. The restore target if the bundle needs a native Codex symlink or prompt link
