<!-- generated: 2026-07-20 | sources: shadowrocket/claude.list, shadowrocket/claude-extended.list, Anthropic/Claude 官方文档, Claude Code 2.1.209 -->

# Claude 分流规则迭代

## 目标

- 为 Shadowrocket 补充 Claude 网页端、移动/桌面 App、Claude Code CLI/IDE 和 Anthropic API 的分流规则。
- 覆盖登录、静态资源、文件上传、实时连接及必要的第三方功能依赖。
- 以当前官方资料为主，避免共享根域、整段 ASN 和域名关键字造成误代理。

## 已核对

- 当前仓库提交：`ad5b61b1046a5d3569b83c598a7c8869a905de10`。
- `shadowrocket/claude.list` 已存在但内容为空，没有既存规则可继承。
- 项目不存在 Claude 相关 feature 文档，无需做 feature 与代码一致性校验。

## 规则依据

- Anthropic 官方 Claude Code 企业网络文档列出的 API、Claude 账号、Console、MCP 代理、下载更新、插件存储、Artifact、Chrome WebSocket 与发行说明端点。
- Anthropic 官方 Claude Desktop 网络要求列出的六组根域，以及动态预览、用户内容和 MCP 内容通配域。
- 本机 Claude Code `2.1.209` 官方程序中可验证的 Anthropic/Claude 服务端点与可选 Datadog 遥测端点。
- `claude.list` 仅保留 Anthropic/Claude 一方核心域名。
- `claude-extended.list` 放置 Google 登录、Claude Code 插件/发行说明共享依赖、Microsoft 365 Add-in 和可选遥测规则，需与核心文件一起加载。
- 已删除没有当前官方依据的 Fathom 端点；Google OAuth token 和云厂商推理端点仅用于特定第三方部署，不进入通用规则。
- 未加入 Bedrock、Vertex AI、Microsoft Foundry 等依赖用户部署区域或网关的云厂商域名，避免把共享云服务整体代理。

## 验证

- 两份规则的类型、字段数和域名格式校验通过。
- `claude.list`：6 条 `DOMAIN-SUFFIX`，共 6 条。
- `claude-extended.list`：7 条 `DOMAIN`，共 7 条。
- 核心与扩展文件没有重复规则；当前官方清单的 22 个代表性端点全部命中。
