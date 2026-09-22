## Why

CodeReview 插件已在独立仓库交付源码和离线 CI，但尚未进入 Full Stack 插件市场，用户无法通过统一目录发现和安装它。市场遵循不可变版本安装，登记前需要补齐插件仓的发布材料。

## What Changes

- 为 `codereview-plugin` 补齐仓库级 Codex 市场清单、三端一致的产品描述和独立徽标。
- 发布可追溯的 `v0.1.0` tag 与 GitHub Release，说明离线已验证和真实宿主/模型尚未验证的边界。
- 将 CodeReview 登记到 `catalog.json`，生成 Codex、ZCode、Kimi 三份市场清单，并更新中英文导航与安装示例。
- 验证源码 tag、Release、市场版本、插件清单和徽标均指向同一发布版本。

## Capabilities

### New Capabilities

- `consent-based-review-distribution`: 用户从统一市场发现并安装独立的可选提交语义审查插件，且能看清其与 CodeGuard、FlowGuard 的职责及验证状态。

### Modified Capabilities

无；沿用现有 `immutable-plugin-installation` 规格。

## Impact

影响 `full-stack-plugins` 的 catalog、三端生成清单和双语 README，以及 `full-stack-plugins/codereview-plugin` 的发布元数据与资产。不会修改 FlowGuard 或 CodeGuard 的运行时。
