# Upstream Installation Notes

This file records the original install instructions or source location for each upstream skill source. The bootstrap repo should consume the manifest here, not rediscover these instructions dynamically.

## `web-access`

- Source repo: `https://github.com/eze-is/web-access.git`
- Original install method: clone the repository and copy `SKILL.md` into `~/.claude/skills/web-access`
- Direct reference: `git clone https://github.com/eze-is/web-access ~/.claude/skills/web-access`

## `superpowers`

- Source repo: `https://github.com/obra/superpowers.git`
- Original Codex install instruction from the upstream README:

```text
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.codex/INSTALL.md
```

## `frontend-design`

- Source repo: `https://github.com/anthropics/claude-plugins-official.git`
- Upstream Claude Code install instruction:

```text
/plugin install frontend-design@claude-plugins-official
```

- Codex extraction path: `plugins/frontend-design/skills/frontend-design`

## `anthropics/skills`

- Source repo: `https://github.com/anthropics/skills.git`
- Upstream Claude Code install instruction:

```text
/plugin marketplace add anthropics/skills
/plugin install document-skills@anthropic-agent-skills
```

- Codex extraction paths: `skills/<skill-name>`

## Rule

When adding a new source, record:

1. The upstream repository URL
2. The upstream install command or source path
3. The Codex extraction path in `skills.manifest.json`
