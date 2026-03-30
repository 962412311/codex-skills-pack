---
name: codex-workspace
description: Work safely inside the Codex + WSL workspace, especially when managing repo-local changes and Linux-side tooling.
---

# Codex Workspace

Use this skill when working inside the repository or the WSL home directory.

## Rules

- Prefer Linux file paths for development work inside WSL.
- Keep project files under the Linux filesystem when possible.
- Avoid mixing Windows-installed npm global binaries with Linux-installed tooling.
- Use the repository manifest as the source of truth for bootstrap content.

## Good Habits

- Keep bootstrap scripts idempotent.
- Make changes in small, auditable units.
- Update the manifest whenever a skill is added or removed.

