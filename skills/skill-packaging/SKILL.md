---
name: skill-packaging
description: Add, package, and validate Codex skills in this repository so they can be installed automatically.
---

# Skill Packaging

Use this skill when adding a new skill or changing an existing one.

## Packaging Rules

- Create one folder per skill.
- Put the main skill instructions in `SKILL.md`.
- Keep the skill focused on one job.
- Add the new skill to `skills.manifest.json`.

## Validation Steps

1. Confirm the folder name matches the manifest name.
2. Confirm `SKILL.md` has valid front matter.
3. Confirm the skill description tells the agent when to use it.
4. Re-run the installer and make sure the skill lands in the WSL Codex skill directory.

