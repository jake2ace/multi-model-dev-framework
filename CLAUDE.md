# Claude 接入约定

[English](docs/CLAUDE.en.md)

当前只预留文档接口，没有 Claude 适配器或已启用的运行配置。
接入前核验账户、CLI 模型 ID 和 effort 支持；展示名称不代表模型已可用。

先读取 AGENTS.md、docs/workflow.md 和当前工程指定的 PROJECT_CONTEXT.md / WORKFLOW_PROFILE.md。
Claude 可按配置担任总控、执行者、审查者或接管者，并不固定只能执行与审查。
若担任总控，就是唯一与开发者对话、决定方向和分发的角色；其他角色通过文件汇报，不直接对接人。
Fable、Opus、Sonnet 是开发者可能选择的名称，不自动解析或替换为其他模型。

## 可选的混合配置示例（未启用）

- Astra 总控，Luna 执行低等级任务，Opus 审 Luna。
- Sonnet 执行其余任务，Sol 审 Sonnet。
- 修改最多 3 次仍未通过，Opus 与 Sol 讨论，总控处理分歧。
- Sonnet 线由 Opus 接管并交 Sol 审；Luna 线由 Sol 接管并交 Opus 审。
- 最终审核者也过目；接管后仍失败则暂停由开发者决定。

以上仅示例。启动前通过协作配置确认实际分工；也可选择 Sol 或 Claude 作为总控，不能把示例当成固定规则。
产出写 outputs，审查写 reviews，摘要写 summaries。只加载任务必要的 skills 与上下文。
不假设 Claude 拥有其他提供方的专属能力；无法满足项目要求时向总控报告。

按协作配置选择中文或英文，只读取一个等价版本。context-mode 的使用与更新入口见 `docs/context-mode.md`；不把查看更新当作升级授权。
对本框架仓库的修改只通过工作分支和 PR 提交；最终合并由所有者决定，代理不得推送 main、合并 PR 或启用自动合并。
