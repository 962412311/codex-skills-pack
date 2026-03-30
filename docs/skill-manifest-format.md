# Skill Manifest Format

`skills.manifest.json` is a declarative install manifest.

The manifest has two layers:

- `sources`: upstream repositories that may be cloned
- `skills`: the individual skill folders to copy into Codex

## Source fields

Each source supports these fields:

- `id`: unique source identifier
- `type`: currently `git`
- `repo`: upstream repository URL
- `ref`: branch, tag, or commit to clone

## Skill fields

Each skill supports these fields:

- `name`: the target skill directory name
- `sourceId`: the source entry to clone
- `sourcePath`: repository-relative path to the skill source
- `enabled`: whether the installer should copy it
- `description`: human-readable summary for maintainers

Recommended repository convention:

```text
skills/<skill-name>/SKILL.md
skills/<skill-name>/README.md   (optional)
```

Plugin-backed skills can also live under a plugin path, for example:

```text
plugins/<plugin-name>/skills/<skill-name>/SKILL.md
```

The installer clones each source, validates the requested `sourcePath`, and copies each enabled skill folder to the WSL user's Codex skill directory.
