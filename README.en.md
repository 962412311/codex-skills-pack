# Codex Skills Pack

[English](./README.en.md) | [简体中文](./README.md)

This repository is the canonical home for your Codex skills: it keeps upstream source notes and also hosts your future personal skills. It does not perform installation.

The bootstrap repo's mainline script falls back to this repository's `main` branch manifest by default, so extra configuration is usually unnecessary.

Its job is simple:

- tell the bootstrapper which skills to install
- record which upstream repositories provide those skills
- map each skill to the exact upstream path used for Codex installation
- maintain your own personal skills in the same manifest flow
- keep the original install notes for auditability

## What This Is Not

- It is not the Windows bootstrapper
- It is not the Codex installer
- It does not install anything by itself

The actual installer lives in [wsl-codex-bootstrap](https://github.com/962412311/wsl-codex-bootstrap).

## What This Covers

This pack currently tracks 33 skills that bootstrap can install, plus 5 built-in Codex system skills. There are also 4 currently installed Claude plugin packages, but the plugin wrappers themselves do not transfer into Codex. See [`docs/current-state.md`](./docs/current-state.md) and [`docs/plugin-notes.md`](./docs/plugin-notes.md) for the full mapping.

- 33 repository-managed / installable skills
- 5 built-in Codex system skills
- 4 currently installed Claude plugin packages

See [`docs/source-inventory.md`](./docs/source-inventory.md) for the exact repository-managed mapping.

## How It Works With Bootstrap

The bootstrap repository prefers `skills.manifest.json` from this repository's `main` branch and installs the listed skills into Codex's skill directory.

If you want to change sources, update the manifest. You do not need to change the installer logic.

## Original Installation Notes

See [`docs/upstream-installation.md`](./docs/upstream-installation.md).

## Repository Layout

- `skills.manifest.json` - machine-readable manifest consumed by bootstrap
- `docs/` - source inventory, current state, and upstream installation notes
- `skills/` - local helper skills used to maintain this pack, such as `patch-context-hygiene`
