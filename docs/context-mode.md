# context-mode：更新入口与 MCP 使用

[English](context-mode.en.md) | [返回首页](../README.md)

## 查看最新功能与版本

- [上游官方仓库 / 使用说明](https://github.com/mksglu/context-mode)
- [最新正式 Release：自动跳转到上游最新发布](https://github.com/mksglu/context-mode/releases/latest)
- [全部 Releases 与更新说明](https://github.com/mksglu/context-mode/releases)
- [main 分支提交记录](https://github.com/mksglu/context-mode/commits/main/)

以上是直接访问上游的链接；打开时查看其当前内容。本仓库不复制上游代码，也不缓存一个版本号冒充实时状态。
Release 是发布版本，main 的提交不一定已发布。上游有新发布也不代表本机已经安装或需要自动升级。

## 通过哪些 MCP 工具减少上下文输入

[context-mode](https://github.com/mksglu/context-mode) 通过在模型上下文之外处理较大输出、建立索引并按需检索，减少直接送进模型的原始文本。接入成功并在适合的任务中使用时，可以减少上下文与部分 token 消耗；不保证特定的套餐额度或费用降幅。

| 场景 | MCP 工具 |
| --- | --- |
| 执行并仅返回所需结果 | `ctx_execute` |
| 处理文件内容 | `ctx_execute_file` |
| 批量执行并检索结果 | `ctx_batch_execute` |
| 建立资料索引，再按问题查找 | `ctx_index` → `ctx_search` |
| 抓取网页并建立索引 | `ctx_fetch_and_index` → `ctx_search` |
| 查看本会话的使用统计 | `ctx_stats` |
| 排查安装、运行环境及集成问题 | `ctx_doctor` |

完整工具名称可能带平台前缀；以当前会话实际暴露的工具及参数为准，不硬编码一个跨平台名称。
工具定义参考：[上游 MCP 实现](https://github.com/mksglu/context-mode/blob/main/src/server.ts)。

## 可选安装：Skill 会替你执行

使用 [multi-model-dev Skill](skill.md) 启动项目时，它会先说明收益与代价，再让你选择安装、跳过或仅检查已有安装。大输出可能减少上下文输入；代价是依赖、配置维护、可能的延迟及本地索引存储，不能保证套餐额度节省。
选择安装后，Skill 会用宿主工具核验当前客户端与上游方法、保留原配置、执行安装注册并分层验证。需要重启或信任操作时明确记录等待状态，不把“已安装”当成“正在使用”。这不是后台自动安装或更新服务，也不是独立安装程序。

## 推荐工作方式

1. 工程启动前确认是否使用 context-mode，并在协作配置记录必需还是可选。
2. 按上游针对当前客户端的安装说明接入，发现工具后调用 `ctx_doctor` 和 `ctx_stats` 验证；读取统计成功不证明路由 hooks 已启用。
3. 长日志、批量搜索和大文件分析优先通过适合的 context-mode 工具处理，向模型返回完成判断所需的片段；小输入不必为了节省而增加调用。
4. 执行一段真实工作后再次查看 `ctx_stats`，记录同一会话中的上下文指标。保留完整诊断证据，不能为了缩短上下文省略失败信息。
5. 不可用时明确报告；必需则暂停相关任务，可选则按工程已确认的回退规则继续。不能把“已安装”写成“正在使用”。

这些是使用约定，不是本仓库已实现的自动路由或统计采集器。

## 统计与额度的区别

`ctx_stats` 报告的上下文指标，以及上游展示的 token / 金额估算，不能直接当作 Codex 周额度账单，也不能作为节省周额度的百分比。比较时注明会话、来源、单位、基线与估算方法，未知值保持未知。
上游实现含估算换算，参考 [统计实现](https://github.com/mksglu/context-mode/blob/main/src/server.ts)。本框架没有完成节省额度的基准测试。

## 更新边界

点击上面的上游链接查看更新即可；本仓库没有后台轮询、自动通知、自动升级或实时状态面板。
升级前比较已安装版本与目标 Release，阅读兼容性说明；升级后重新核验工具及 hooks。版本查询和安装升级是两件事，不能因查看更新就自动执行 `ctx_upgrade`。

框架与 context-mode 是独立项目；context-mode 遵循[它自己的许可证](https://github.com/mksglu/context-mode/blob/main/LICENSE)。
