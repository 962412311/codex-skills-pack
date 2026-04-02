# Codex Skills Pack

[English](./README.en.md) | [简体中文](./README.md)

这个仓库是你的 Codex skills 主仓，既维护上游来源清单，也承载你后续新增的个人 skills。

bootstrap 仓库的主线脚本会默认回退到这里的 `main` 分支 manifest，所以通常不需要额外配置。

它的作用很直接：

- 告诉 bootstrap 仓库该装哪些 skills
- 记录每个 skill 来自哪个上游仓库
- 说明每个 skill 在上游仓库里的准确路径
- 维护你自己的个人 skills，并把它们纳入同一套 manifest
- 保留原始安装说明，方便审计和维护

## 这不是

- 这不是 Windows bootstrap 仓库
- 这不是 Codex 安装器
- 这不会在本仓库里直接执行安装

真正负责安装的是 [wsl-codex-bootstrap](https://github.com/962412311/wsl-codex-bootstrap)。

## 当前会覆盖什么

这个仓库当前维护 33 个可由 bootstrap 安装的 skills，外加 Codex 自带的 5 个 system skills。当前 Claude 侧还装着 4 个插件包，但插件壳本身不会直接进入 Codex，相关映射见 [`docs/current-state.md`](./docs/current-state.md) 和 [`docs/plugin-notes.md`](./docs/plugin-notes.md)。

- 33 个仓库维护/可安装 skills
- 5 个 Codex 内建 system skills
- 4 个当前已装 Claude 插件包

精确映射见 [`docs/source-inventory.md`](./docs/source-inventory.md)。

## 怎么配合 bootstrap

bootstrap 仓库会优先读取这里 `main` 分支上的 `skills.manifest.json`，然后自动把对应 skills 安装到 Codex 的 skills 目录。

如果你要换来源，只需要改 manifest，不需要改安装器主逻辑。

## 原始安装说明

见 [`docs/upstream-installation.md`](./docs/upstream-installation.md)。

## 仓库结构

- `skills.manifest.json` - bootstrap 消费的机器可读 manifest
- `docs/` - 来源清单、当前状态和原始安装说明
- `skills/` - 用于维护这个仓库的本地 helper skills，例如 `patch-context-hygiene`
