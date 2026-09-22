## Context

参见 proposal.md。`full-stack-plugins/catalog.json` 是聚合清单事实源，`sync-marketplaces.mjs` 生成三端清单并要求每个插件仓具备技能、徽标、三端 manifest 与单插件 Codex 市场清单。`immutable-plugin-installation` 要求来源固定到 tag，远端校验要求正式 GitHub Release。CodeReview v0.1.0 已有源码和 macOS/Linux × Python 3.11/3.13 离线 CI，但缺单插件市场清单、徽标、tag 和 Release。

## Goals / Non-Goals

**Goals:** 让 v0.1.0 可按现有市场规则安装；统一清单与插件元数据；将尚未实测的运行能力写清楚。

**Non-Goals:** 本变更不升级本机 OCR、不进行真实模型调用或三宿主安装，不修改 CodeGuard/FlowGuard 运行时，也不将 CodeReview 的建议变为强制门禁。

## Decisions

1. 沿用插件现有 `codereview-plugin` 标识，避免为市场登记重命名三端 manifest 与既有仓库。导航显示名保留 `CodeReview`，分类为 `Developer Tools`。
2. 在插件仓补齐 `assets/official-logo.png` 与单插件 `.agents/plugins/marketplace.json`，三端描述以 catalog 的英文描述一致；保留仓内 OpenSpec 开发技能不进入分发清单。
3. 先发布含全部资产的插件提交与 `v0.1.0` GitHub Release，再把 `catalog.json` 和生成清单合入市场仓。若插件发布失败，市场不指向未发布版本。
4. 使用仓库自带生成器生成聚合清单，按展示名称排序；中英文 README 的插件数量、目录版本与安装命令从当前 catalog 更新。

## Risks / Trade-offs

- [真实运行未验收] → 在 Release 与插件 README 保留 `UNVERIFIED`，市场文案不声称三端已加载。
- [生成器可能改动其他插件] → 发布前后比较全部生成清单差异，仅接受 CodeReview 新条目；不改其他插件仓配置。
- [tag 可被移动] → 发布后核对 tag peeled commit、Release target 与市场 ref；不移动已发布 tag。

## Migration Plan

插件仓补齐分发材料并跑离线 CI；发布 v0.1.0；市场仓登记并生成三端清单，运行本地及远端发布校验、提交推送并核对 CI。若市场校验失败，保持当前市场版本不变，修复插件仓后重试；已发布 tag 不重写。
