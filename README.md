# Codex Skills Pack

[English](./README.md) | [简体中文](./README.zh.md)

This repository maintains the Codex skill inventory that is consumed by the WSL bootstrap repo.

It is responsible for:

- declaring which upstream repositories provide which skills
- recording the original installation instructions from the source projects
- keeping the Codex-specific copy paths in one place
- serving as the single manifest source for the bootstrapper

## What This Is Not

- It is not the Windows bootstrapper
- It is not the Codex installer
- It does not configure WSL, Node.js, or `@openai/codex`

Those responsibilities live in [wsl-codex-bootstrap](https://github.com/962412311/wsl-codex-bootstrap).

## Quick Start

1. Clone this repository.
2. Review or edit [`skills.manifest.json`](./skills.manifest.json).
3. Keep the manifest in sync with the sources you want Codex to install.
4. Point the bootstrap repository at this manifest, either via `skills-source.json` or the `-SkillsManifestPath` override.

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

## Public Release

After publishing this repository, update the bootstrap repo's `skills-source.json` to the raw GitHub URL for this manifest.

Recommended naming:

- `codex-skills-pack` for this repository
- `wsl-codex-bootstrap` for the Windows bootstrapper

## Maintenance Rules

- Keep source mappings declarative in `skills.manifest.json`.
- Preserve canonical source selection for duplicate skills such as `frontend-design`.
- Document any new source in `docs/upstream-installation.md` before wiring it into the bootstrap flow.

## Repository Layout

- `skills.manifest.json` - machine-readable manifest consumed by bootstrap
- `docs/` - source inventory and upstream installation notes
- `skills/` - local helper skills used to maintain this pack
