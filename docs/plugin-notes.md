# Plugin Notes

Claude Code plugins are not installed into Codex as plugins.

What this bootstrap does instead:

1. Identifies the useful skills contained inside each current Claude plugin
2. Clones the upstream source repository
3. Copies the relevant `SKILL.md` folders into `~/.codex/skills`

## Current Claude Plugin Mapping

- `superpowers@obra`
  - Source repo: `https://github.com/obra/superpowers.git`
  - Installed skills: the 14 `superpowers` skills

- `frontend-design@claude-plugins-official`
  - Source repo: `https://github.com/anthropics/claude-plugins-official.git`
  - Installed skill: `frontend-design`
  - Canonical source selected for this repository

- `document-skills@anthropic-agent-skills`
  - Source repo: `https://github.com/anthropics/skills.git`
  - Installed skills: the 16 document and technical skills listed in `docs/source-inventory.md`
  - Excluded skill: `frontend-design` from this repo, because the canonical copy comes from `claude-plugins-official`

## Why This Works

Codex consumes skills as folders on disk. The bootstrap repo focuses on the skill content and ignores Claude-specific plugin packaging, because that packaging is not portable to Codex.
