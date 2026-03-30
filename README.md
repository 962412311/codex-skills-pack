# Codex Skills Pack

This repository maintains the Codex skill inventory that is consumed by the WSL bootstrap repo.

It is responsible for:

- declaring which upstream repositories provide which skills
- recording the original installation instructions from the source projects
- keeping the Codex-specific copy paths in one place

## What This Is Not

- It is not the Windows bootstrapper
- It is not the Codex installer
- It does not configure WSL, Node.js, or `@openai/codex`

Those responsibilities live in [`wsl-codex-bootstrap`](../wsl-codex-bootstrap).

## Sources

This pack currently tracks:

- `web-access` from `eze-is/web-access`
- the 14 `superpowers` skills from `obra/superpowers`
- `frontend-design` from `anthropics/claude-plugins-official`
- document and technical skills from `anthropics/skills`

See [`docs/source-inventory.md`](./docs/source-inventory.md) for the exact skill mapping.

## Installation Model

The bootstrap repo reads `skills.manifest.json` from this repository or from a published raw URL.

The manifest lists the upstream Git repositories and the exact path for each installable skill folder.

## Original Installation Notes

See [`docs/upstream-installation.md`](./docs/upstream-installation.md) for the upstream install commands and source references.

## Repository Layout

- `skills.manifest.json` - machine-readable manifest consumed by bootstrap
- `docs/` - source inventory and upstream installation notes
- `skills/` - local helper skills used to maintain this pack
