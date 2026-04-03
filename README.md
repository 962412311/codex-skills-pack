# Codex Skills Pack

[English](./README.en.md) | 简体中文

Codex/Claude Code 的 skill 和 plugin 统一清单仓库。维护上游来源映射、安装路径，以及自建 skills。

## 快速安装（无需 bootstrap）

在没有 wsl-codex-bootstrap 的环境下，可以直接用以下步骤手动安装：

```bash
# 1. 克隆所有上游仓库到临时目录
mkdir -p /tmp/codex-skill-install && cd /tmp/codex-skill-install
git clone --depth 1 https://github.com/962412311/codex-skills-pack.git
git clone --depth 1 https://github.com/eze-is/web-access.git
git clone --depth 1 https://github.com/obra/superpowers.git
git clone --depth 1 https://github.com/anthropics/claude-plugins-official.git
git clone --depth 1 https://github.com/anthropics/skills.git
git clone --depth 1 https://github.com/tanweai/pua.git

# 2. 同步所有 skills 到 ~/.codex/skills/
# web-access
rsync -a web-access/ ~/.codex/skills/web-access/
# superpowers 14 个 skills
for s in brainstorming dispatching-parallel-agents executing-plans finishing-a-development-branch receiving-code-review requesting-code-review subagent-driven-development systematic-debugging test-driven-development using-git-worktrees using-superpowers verification-before-completion writing-plans writing-skills; do
  rsync -a "superpowers/skills/$s/" ~/.codex/skills/$s/
done
# frontend-design (来自 claude-plugins-official，非 anthropics/skills)
rsync -a claude-plugins-official/plugins/frontend-design/skills/frontend-design/ ~/.codex/skills/frontend-design/
# anthropic agent skills 16 个
for s in algorithmic-art brand-guidelines canvas-design claude-api doc-coauthoring docx internal-comms mcp-builder pdf pptx skill-creator slack-gif-creator theme-factory web-artifacts-builder webapp-testing xlsx; do
  rsync -a "skills/skills/$s/" ~/.codex/skills/$s/
done
# 自建 skill
rsync -a codex-skills-pack/skills/patch-context-hygiene/ ~/.codex/skills/patch-context-hygiene/

# 3. 安装 plugins（完整包，含 hooks/agents/commands 等）
rsync -a superpowers/ ~/.codex/superpowers/
rsync -a pua/ ~/.codex/pua/

# 4. 建立符号链接
mkdir -p ~/.agents/skills ~/.codex/prompts
ln -sf ~/.codex/superpowers/skills ~/.agents/skills/superpowers
ln -sf ~/.codex/pua/codex/pua ~/.codex/skills/pua
ln -sf ~/.codex/pua/commands/pua.md ~/.codex/prompts/pua.md

# 5. 清理
rm -rf /tmp/codex-skill-install
```

也可以直接让 Claude Code 执行安装：把本仓库路径或 URL 给它，说"帮我安装所有 skill 和 plugin"即可。

## Skills 清单（33 个）

| 来源 | Skills |
|------|--------|
| **eze-is/web-access** | `web-access` |
| **obra/superpowers** | `brainstorming`, `dispatching-parallel-agents`, `executing-plans`, `finishing-a-development-branch`, `receiving-code-review`, `requesting-code-review`, `subagent-driven-development`, `systematic-debugging`, `test-driven-development`, `using-git-worktrees`, `using-superpowers`, `verification-before-completion`, `writing-plans`, `writing-skills` |
| **anthropics/claude-plugins-official** | `frontend-design` |
| **anthropics/skills** | `algorithmic-art`, `brand-guidelines`, `canvas-design`, `claude-api`, `doc-coauthoring`, `docx`, `internal-comms`, `mcp-builder`, `pdf`, `pptx`, `skill-creator`, `slack-gif-creator`, `theme-factory`, `web-artifacts-builder`, `webapp-testing`, `xlsx` |
| **codex-skills-pack (本仓库)** | `patch-context-hygiene` |

## Plugins 清单（4 个）

| Plugin | 上游仓库 | 安装位置 | 链接 |
|--------|----------|----------|------|
| superpowers | obra/superpowers | `~/.codex/superpowers/` | `~/.agents/skills/superpowers` → `skills/` |
| pua | tanweai/pua | `~/.codex/pua/` | `~/.codex/skills/pua` → `codex/pua/`, `~/.codex/prompts/pua.md` → `commands/pua.md` |
| frontend-design | anthropics/claude-plugins-official | `~/.codex/skills/frontend-design/` | — |
| document-skills | anthropics/skills | `~/.codex/skills/{各 skill}/` | — |

## 配合 bootstrap 使用

bootstrap 仓库 ([wsl-codex-bootstrap](https://github.com/962412311/wsl-codex-bootstrap)) 会自动读取本仓库 `main` 分支的 `skills.manifest.json` 和 `plugins.manifest.json` 完成安装。修改来源只需改 manifest，无需改安装器。

## 冲突规则

`frontend-design` 同时存在于 `anthropics/claude-plugins-official` 和 `anthropics/skills`。本仓库统一使用 `claude-plugins-official` 版本（`anthropics/skills` 中的副本已排除）。

## 仓库结构

```
codex-skills-pack/
├── skills.manifest.json      # bootstrap 消费的 skills 清单
├── plugins.manifest.json     # bootstrap 消费的 plugins 清单
├── docs/
│   ├── source-inventory.md   # 上游来源与 skill 映射表
│   ├── current-state.md      # 当前已安装状态快照
│   ├── plugin-notes.md       # 插件映射说明
│   └── upstream-installation.md  # 原始安装说明
└── skills/                   # 自建本地 skills
    └── patch-context-hygiene/
```

## 这不是

- 不是 Windows bootstrap 仓库
- 不是 Codex 安装器
- 不在本仓库内执行安装（安装由 bootstrap 或手动完成）
