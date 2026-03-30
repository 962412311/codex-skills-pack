# Codex Skills Pack

[English](./README.en.md) | [简体中文](./README.md)

This repository only maintains the Codex skill manifest and source notes. It does not perform installation.

Its job is simple:

- tell the bootstrapper which skills to install
- record which upstream repositories provide those skills
- map each skill to the exact upstream path used for Codex installation
- keep the original install notes for auditability

## What This Is Not

- It is not the Windows bootstrapper
- It is not the Codex installer
- It does not install anything by itself

The actual installer lives in [wsl-codex-bootstrap](https://github.com/962412311/wsl-codex-bootstrap).

## What Gets Installed

This pack currently tracks 32 enabled skills:

- `web-access`
- 14 `superpowers` skills
- `frontend-design`
- 16 document and technical skills

See [`docs/source-inventory.md`](./docs/source-inventory.md) for the exact mapping.

## How It Works With Bootstrap

The bootstrap repository reads `skills.manifest.json` from here and installs the listed skills into Codex's skill directory.

If you want to change sources, update the manifest. You do not need to change the installer logic.

## Original Installation Notes

See [`docs/upstream-installation.md`](./docs/upstream-installation.md).

## Repository Layout

- `skills.manifest.json` - machine-readable manifest consumed by bootstrap
- `docs/` - source inventory and upstream installation notes
- `skills/` - local helper skills used to maintain this pack
