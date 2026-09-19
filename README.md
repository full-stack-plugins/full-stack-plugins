<div align="center">

# Full Stack Plugins

**4 个插件。研发全流程。一个统一生态。**

*AI 设计工具 · 图表绘制 · 代码质量 · 服务器运维 — 生产级品质，Codex / ZCode / Kimi 三平台独立安装。*

[![License](https://img.shields.io/badge/License-Apache%202.0-green)](LICENSE)
[![Platforms](https://img.shields.io/badge/hosts-Codex%20%C2%B7%20ZCode%20%C2%B7%20Kimi-blue)](#-安装)
[![Plugins](https://img.shields.io/badge/plugins-4-green)](#-插件目录)

[English](./README.en.md)

[简介](#-简介) ·
[安装](#-安装) ·
[插件目录](#-插件目录) ·
[架构](#-架构) ·
[生态](#-生态) ·
[贡献](#-贡献指南)

</div>

---

## 简介

**Full Stack Plugins** 是面向研发过程的插件市场，覆盖 AI 设计工具、图表绘制、代码质量与服务器运维，面向 Codex、ZCode 与 Kimi Code 三个宿主平台。

本仓库与技能侧的 [Full Stack Skills](https://github.com/partme-ai/full-stack-skills) 对位：技能侧沉淀「怎么想」的领域知识（框架、架构、测试方法论），插件侧提供「能做到」的可执行能力（MCP 工具、门禁流水线、自动化运维）。两者按同一套领域划分共建同一个生态——Stitch 对应技能侧的 stitch-skills，ProcessOn 对应 processon-skills。

> 本仓库只包含市场元数据（catalog 与三平台清单），不包含插件运行时代码。每个插件在各自独立仓库中维护，通过 `catalog.json` 单一事实源对齐 ID、名称、版本、分类与仓库地址。

### 覆盖领域

| 领域 | 问题 | 解决方案（插件） |
|------|------|------------------|
| **AI 设计工具** | UI 设计稿生成与前端落地 | stitch-design |
| **图表绘制** | 流程图、架构图、思维导图 | processon-design |
| **代码质量** | 让 AI 写的代码一次通过 lint 门禁 | codeguard |
| **服务器运维** | 宝塔面板站点 / 数据库 / 计划任务 | bt-linux-panel |

---

## 安装

### Codex

```bash
codex plugin marketplace add partme-ai/full-stack-plugins
codex plugin add bt-linux-panel@full-stack-plugins
codex plugin add codeguard@full-stack-plugins
codex plugin add processon-design@full-stack-plugins
codex plugin add stitch-design@full-stack-plugins
```

### ZCode

打开 设置 → 插件 → 创建 → 添加插件市场，输入 `partme-ai/full-stack-plugins`，然后在个人市场分区中安装。

### Kimi Code CLI

```text
/plugins marketplace https://raw.githubusercontent.com/partme-ai/full-stack-plugins/main/kimi-marketplace.json
```

---

## 插件目录

| 插件 | ID | 版本 | 定位 | 仓库 |
|------|----|:----:|------|------|
| 🛡️ **宝塔 Linux 面板** | `bt-linux-panel` | 1.0.1 | 通过 MCP 运维宝塔 Linux 面板 | [partme-bt-plugin](https://github.com/full-stack-plugins/partme-bt-plugin) |
| 🔍 **代码规范守卫** | `codeguard` | 0.3.4 | 让 AI 写的代码一次通过 lint 门禁（多语言规则集） | [partme-codeguard-plugin](https://github.com/full-stack-plugins/partme-codeguard-plugin) |
| 📊 **ProcessOn 图表** | `processon-design` | 0.2.1 | 生成可编辑的 ProcessOn 精美图表（流程图 / 架构图 / 思维导图） | [partme-processon-plugin](https://github.com/full-stack-plugins/partme-processon-plugin) |
| 🎨 **Google Stitch 设计** | `stitch-design` | 0.7.9 | 基于 Google Stitch 的设计与前端搭建 | [partme-stitch-plugin](https://github.com/full-stack-plugins/partme-stitch-plugin) |

---

## 架构

### 市场如何工作

`catalog.json` 是唯一事实源。`scripts/sync-marketplaces.mjs` 从它生成三平台清单，并校验每个插件仓的 skills 目录（frontmatter、命名一致性）：

```
full-stack-plugins/
├── catalog.json                        # 单一事实源：ID / 名称 / 版本 / 分类 / 仓库
├── .agents/plugins/marketplace.json    # Codex 清单（生成物）
├── marketplace.json                    # ZCode 清单（生成物）
├── kimi-marketplace.json               # Kimi 清单（生成物）
└── scripts/                            # 同步与发版工具
```

每个独立插件仓负责自己的运行时适配：`.codex-plugin/plugin.json`、`.zcode-plugin/plugin.json` 与 `kimi.plugin.json`。

### 渐进式披露

插件内的技能遵循 [Agent Skills 规范](https://agentskills.io)：

1. **启动时**：仅加载技能名称和描述（最小上下文）
2. **按需**：当智能体识别到相关任务时加载完整的 `SKILL.md`
3. **深入**：仅在明确需要时读取参考文件

---

## 生态

| 资源 | 链接 |
|------|------|
| **技能侧导航（全栈）** | [partme-ai/full-stack-skills](https://github.com/partme-ai/full-stack-skills) |
| **技能包组织（全栈）** | [github.com/full-stack-skills](https://github.com/full-stack-skills) |
| **AIGC 侧插件市场** | [github.com/full-aigc-plugins](https://github.com/full-aigc-plugins) |
| **AIGC 侧技能导航** | [partme-ai/full-aigc-skills](https://github.com/partme-ai/full-aigc-skills) |
| **Agent Skills 规范** | [agentskills.io](https://agentskills.io) |
| **Skills CLI** | [github.com/vercel-labs/skills](https://github.com/vercel-labs/skills) |
| **PartMe.AI** | [github.com/partme-ai](https://github.com/partme-ai) |

---

## 贡献指南

### 发版纪律

任何插件代码改动（无论大小）都要 bump + 发版，市场端靠版本号感知更新：

```bash
node scripts/bump-plugin.mjs <plugin-id> <major|minor|patch>
```

该命令会同步更新 catalog 版本、插件仓四个 manifest，并重新生成三平台清单。

### 新增插件

1. 在独立仓库中按三平台适配层构建插件（`.codex-plugin` / `.zcode-plugin` / `kimi.plugin.json`）
2. 在 `catalog.json` 中登记条目
3. 运行 `node scripts/sync-marketplaces.mjs --write` 重新生成清单并提交

---

## 许可证

Apache 2.0 — 详见 [LICENSE](LICENSE)。

---

<div align="center">

**如果这个项目对你有帮助，请给我们一个 ⭐️**

Made with ❤️ by PartMe.AI Team

</div>
