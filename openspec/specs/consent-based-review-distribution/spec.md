# consent-based-review-distribution Specification

## Purpose
让用户在统一的 Full Stack 插件市场中找到可选提交语义审查插件，明确其授权与建议性质，并从可追溯的正式版本安装三端适配包。
## Requirements
### Requirement: 统一市场可发现 CodeReview
市场 SHALL 在 Codex、ZCode 与 Kimi 清单中列出 CodeReview 插件，并提供一致的标识、版本、独立仓库来源和语义审查简介。中英文导航 SHALL 给出安装入口并区分 CodeReview、CodeGuard、FlowGuard 的职责。

#### Scenario: 用户浏览插件市场
- **WHEN** 用户查看任一宿主的 Full Stack 插件清单
- **THEN** 用户能找到 CodeReview 及其正式版本来源，并知道它需要提交前授权、输出建议性风险报告

### Requirement: 发布身份与素材一致
CodeReview 的市场条目 MUST 指向含实际插件代码和徽标的版本 tag；对应仓库 MUST 存在该 tag 的正式 GitHub Release。聚合清单与仓库级清单 MUST 使用同一版本，且三个宿主 manifest MUST 声明一致的基础版本和产品描述。

#### Scenario: 准备登记未发布版本
- **WHEN** 版本 tag、Release、徽标或某个宿主 manifest 缺失或不一致
- **THEN** 市场校验失败，该版本不得作为可安装条目发布

#### Scenario: 三端安装已发布版本
- **WHEN** 用户从 Codex、ZCode 或 Kimi 市场选择 CodeReview
- **THEN** 安装来源固定到同一正式发布版本，不随默认分支后续提交漂移

### Requirement: 验证边界可见
市场与插件文档 MUST 区分离线测试、真实 OCR 审查和宿主实际加载的验证状态，不能把源码发布或 CI 成功表述为三端运行验收通过。

#### Scenario: 初始版本仅完成离线验证
- **WHEN** v0.1.0 发布时尚未完成真实模型与三宿主加载测试
- **THEN** 发布说明和插件文档明确标记这些能力为未验证，且不声称 CodeReview 可以替代 FlowGuard 或 CodeGuard 的裁决
