---
name: repo-maintenance
description: Maintain the public bootstrap repository, version its contents, and keep the documented install flow aligned with reality.
---

# Repository Maintenance

Use this skill when updating the public bootstrap repository.

## Rules

- Keep the repository self-contained.
- Keep the README and manifest in sync with the installer.
- Prefer explicit declarative configuration over hard-coded lists.
- When a new skill is added, document why it exists and who should use it.

## Review Checklist

1. Does the installer still work from a clean machine?
2. Does the manifest still describe every packaged skill?
3. Are the docs still consistent with the script flags?
4. Did any change accidentally make the repo Windows-only or distro-specific?

