# Codex Skills Pack

English | [简体中文](./README.md)

A unified manifest repository for Codex / Claude Code skills and plugins. Maintains upstream source mappings, install paths, and locally authored skills.

## Quick Install (without bootstrap)

On machines without wsl-codex-bootstrap, install manually:

```bash
# 1. Clone all upstream repos to a temp directory
mkdir -p /tmp/codex-skill-install && cd /tmp/codex-skill-install
git clone --depth 1 https://github.com/962412311/codex-skills-pack.git
git clone --depth 1 https://github.com/eze-is/web-access.git
git clone --depth 1 https://github.com/obra/superpowers.git
git clone --depth 1 https://github.com/anthropics/claude-plugins-official.git
git clone --depth 1 https://github.com/anthropics/skills.git
git clone --depth 1 https://github.com/tanweai/pua.git

# 2. Sync all skills into ~/.codex/skills/
# web-access
rsync -a web-access/ ~/.codex/skills/web-access/
# superpowers (14 skills)
for s in brainstorming dispatching-parallel-agents executing-plans finishing-a-development-branch receiving-code-review requesting-code-review subagent-driven-development systematic-debugging test-driven-development using-git-worktrees using-superpowers verification-before-completion writing-plans writing-skills; do
  rsync -a "superpowers/skills/$s/" ~/.codex/skills/$s/
done
# frontend-design (from claude-plugins-official, NOT anthropics/skills)
rsync -a claude-plugins-official/plugins/frontend-design/skills/frontend-design/ ~/.codex/skills/frontend-design/
# anthropic agent skills (16)
for s in algorithmic-art brand-guidelines canvas-design claude-api doc-coauthoring docx internal-comms mcp-builder pdf pptx skill-creator slack-gif-creator theme-factory web-artifacts-builder webapp-testing xlsx; do
  rsync -a "skills/skills/$s/" ~/.codex/skills/$s/
done
# local skill
rsync -a codex-skills-pack/skills/patch-context-hygiene/ ~/.codex/skills/patch-context-hygiene/

# 3. Install plugins (full packages including hooks/agents/commands)
rsync -a superpowers/ ~/.codex/superpowers/
rsync -a pua/ ~/.codex/pua/

# 4. Create symlinks
mkdir -p ~/.agents/skills ~/.codex/prompts
ln -sf ~/.codex/superpowers/skills ~/.agents/skills/superpowers
ln -sf ~/.codex/pua/codex/pua ~/.codex/skills/pua
ln -sf ~/.codex/pua/commands/pua.md ~/.codex/prompts/pua.md

# 5. Cleanup
rm -rf /tmp/codex-skill-install
```

Or simply give Claude Code this repo's path or URL and ask it to "install all skills and plugins".

## Skills Inventory (33)

| Source | Skills |
|--------|--------|
| **eze-is/web-access** | `web-access` |
| **obra/superpowers** | `brainstorming`, `dispatching-parallel-agents`, `executing-plans`, `finishing-a-development-branch`, `receiving-code-review`, `requesting-code-review`, `subagent-driven-development`, `systematic-debugging`, `test-driven-development`, `using-git-worktrees`, `using-superpowers`, `verification-before-completion`, `writing-plans`, `writing-skills` |
| **anthropics/claude-plugins-official** | `frontend-design` |
| **anthropics/skills** | `algorithmic-art`, `brand-guidelines`, `canvas-design`, `claude-api`, `doc-coauthoring`, `docx`, `internal-comms`, `mcp-builder`, `pdf`, `pptx`, `skill-creator`, `slack-gif-creator`, `theme-factory`, `web-artifacts-builder`, `webapp-testing`, `xlsx` |
| **codex-skills-pack (this repo)** | `patch-context-hygiene` |

## Plugins Inventory (4)

| Plugin | Upstream repo | Install location | Links |
|--------|---------------|------------------|-------|
| superpowers | obra/superpowers | `~/.codex/superpowers/` | `~/.agents/skills/superpowers` → `skills/` |
| pua | tanweai/pua | `~/.codex/pua/` | `~/.codex/skills/pua` → `codex/pua/`, `~/.codex/prompts/pua.md` → `commands/pua.md` |
| frontend-design | anthropics/claude-plugins-official | `~/.codex/skills/frontend-design/` | — |
| document-skills | anthropics/skills | `~/.codex/skills/{individual skills}/` | — |

## Using with bootstrap

The bootstrap repo ([wsl-codex-bootstrap](https://github.com/962412311/wsl-codex-bootstrap)) reads `skills.manifest.json` and `plugins.manifest.json` from this repo's `main` branch automatically. To change sources, update the manifests — no installer changes needed.

## Conflict Rule

`frontend-design` exists in both `anthropics/claude-plugins-official` and `anthropics/skills`. This repo uses the `claude-plugins-official` version exclusively (the `anthropics/skills` copy is excluded).

## Repository Layout

```
codex-skills-pack/
├── skills.manifest.json      # machine-readable manifest consumed by bootstrap
├── plugins.manifest.json     # machine-readable plugin manifest
├── docs/
│   ├── source-inventory.md   # upstream source to skill mapping
│   ├── current-state.md      # current install state snapshot
│   ├── plugin-notes.md       # plugin mapping notes
│   └── upstream-installation.md  # original installation instructions
└── skills/                   # locally authored skills
    └── patch-context-hygiene/
```

## What This Is Not

- Not the Windows bootstrap repository
- Not the Codex installer
- Does not execute installation (bootstrap or manual install handles that)
