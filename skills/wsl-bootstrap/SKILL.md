---
name: wsl-bootstrap
description: Bootstrap, repair, and rerun the Windows-to-WSL Codex installation flow on a new machine.
---

# WSL Bootstrap

Use this skill when the task is about:

- installing WSL on a fresh Windows machine
- re-running the bootstrap after a reboot
- diagnosing setup failures

## Rules

- Prefer the repository bootstrap script over manual one-off steps.
- Keep the flow idempotent where possible.
- Record the exact distro and flags used for installation.

## Typical Checks

1. Confirm PowerShell is running as Administrator.
2. Confirm Windows build supports WSL 2.
3. Confirm the target distro is installed and initialized.
4. Confirm Node, `nvm`, and `codex` are available in the Linux user shell.

