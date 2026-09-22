## 1. 插件仓分发准备

- [x] 1.1 为 CodeReview 添加独立徽标和单插件 Codex 市场清单，确保开发用 `.agents/skills` 不进入发布包。
- [x] 1.2 对齐 Codex、ZCode、Kimi 的 v0.1.0 标识、英文描述、展示名和徽标，运行插件与技能校验。
- [x] 1.3 更新插件 README 的真实发布状态与运行验收边界，运行完整离线测试和 OpenSpec 校验。

## 2. 不可变发布

- [x] 2.1 提交并推送插件仓分发材料，核对插件 CI。
- [x] 2.2 为该提交创建不可移动的 v0.1.0 tag 与正式 GitHub Release，核对 tag、Release 和源码提交一致。

## 3. 聚合市场登记

- [x] 3.1 在 `catalog.json` 登记 CodeReview，生成三端市场清单，仅新增目标插件条目。
- [x] 3.2 更新中英文 README 的插件数量、安装命令和职责说明，保持已有版本与 catalog 一致。
- [x] 3.3 运行本地和远端市场校验、OpenSpec strict validation；提交推送市场仓，核对远端内容与干净工作区。市场仓未配置 CI。
