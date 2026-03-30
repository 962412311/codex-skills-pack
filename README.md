# Codex Skills Pack

[English](./README.en.md) | [简体中文](./README.md)

这个仓库维护 Codex 的 skills 清单，会被 WSL bootstrap 仓库消费。

它负责：

- 声明每个 skill 来自哪个上游仓库
- 记录来源项目里的原始安装说明
- 统一管理 Codex 侧的复制路径
- 作为 bootstrap 的唯一 manifest 来源

## 这不是

- 这不是 Windows bootstrap 仓库
- 这不是 Codex 安装器
- 这不负责配置 WSL、Node.js 或 `@openai/codex`

这些职责属于 [wsl-codex-bootstrap](https://github.com/962412311/wsl-codex-bootstrap)。

## 快速开始

1. 克隆这个仓库。
2. 查看或修改 [`skills.manifest.json`](./skills.manifest.json)。
3. 保持 manifest 与你希望 Codex 安装的来源一致。
4. 通过 `skills-source.json` 或 `-SkillsManifestPath` 让 bootstrap 指向这个 manifest。

## 来源

当前维护的来源包括：

- `web-access`，来自 `eze-is/web-access`
- 14 个 `superpowers` skills，来自 `obra/superpowers`
- `frontend-design`，来自 `anthropics/claude-plugins-official`
- 文档和技术类 skills，来自 `anthropics/skills`

精确的映射关系见 [`docs/source-inventory.md`](./docs/source-inventory.md)。

## 安装模型

bootstrap 仓库会从这里读取 `skills.manifest.json`，或者读取公开的 raw URL。

manifest 里定义了上游 Git 仓库，以及每个可安装 skill 的准确路径。

## 原始安装说明

见 [`docs/upstream-installation.md`](./docs/upstream-installation.md)。

## 公开发布

发布这个仓库之后，把 bootstrap 的 `skills-source.json` 指向这里的 raw GitHub URL。

建议命名：

- `codex-skills-pack` 作为这个仓库名
- `wsl-codex-bootstrap` 作为 Windows bootstrap 仓库名

## 维护规则

- 保持 `skills.manifest.json` 里的来源映射是声明式的
- 对于重名 skill，保留 canonical source，例如 `frontend-design`
- 新增来源前，先在 `docs/upstream-installation.md` 记录

## 仓库结构

- `skills.manifest.json` - bootstrap 消费的机器可读 manifest
- `docs/` - 来源清单和原始安装说明
- `skills/` - 用于维护这个仓库的本地 helper skills
