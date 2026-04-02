# Plugin Notes

Claude Code plugins are not installed into Codex as plugins.

What this bootstrap does instead:

1. Identifies the useful skills contained inside each current Claude plugin
2. Replays the upstream install rule for each bundle:
   - marketplace-style plugins are restored from their upstream marketplace repos into the Claude cache
   - native skill bundles such as `superpowers` and `pua` are cloned into `~/.codex/...` and linked the way their upstream `INSTALL.md` files describe
3. Copies the relevant `SKILL.md` folders into `~/.codex/skills`

## Current Claude Plugin Mapping

| Installed plugin | Source repo | Version | Codex-visible result |
|---|---|---|---|
| `superpowers@claude-plugins-official` | `https://github.com/obra/superpowers.git` | `5.0.6` | 14 workflow skills under the Codex skill tree |
| `frontend-design@claude-plugins-official` | `https://github.com/anthropics/claude-plugins-official.git` | `unknown` | canonical `frontend-design` skill |
| `document-skills@anthropic-agent-skills` | `https://github.com/anthropics/skills.git` | `98669c11ca63` | the 16 document and technical skills listed in `docs/source-inventory.md` |
| `pua@pua-skills` | `https://github.com/tanweai/pua.git` | `3.1.0` | a separate plugin bundle with its own skills and commands; not part of the 33-skill bootstrap manifest |

## Why This Works

Codex consumes skills as folders on disk. The bootstrap repo now preserves the upstream install semantics where needed, but still treats the resulting folders as the portable source of truth for Codex.

For the exact current install snapshot, see [`docs/current-state.md`](./current-state.md).
