<!-- generated: 2026-07-20 | sources: shadowrocket/openai.list, shadowrocket/openai-extended.list, OpenAI 官方网络文档 -->

# OpenAI 分流规则迭代

## 目标

- 为 Shadowrocket 补充 OpenAI、ChatGPT 与 Codex 的网页、App、桌面软件和终端流量规则。
- 规则采用 Shadowrocket `DOMAIN`、`DOMAIN-SUFFIX` 等兼容格式。
- 优先使用可验证的官方域名，并控制第三方依赖域名的误代理范围。

## 已核对

- 当前仓库提交：`ad5b61b1046a5d3569b83c598a7c8869a905de10`。
- `shadowrocket/openai.list` 当前只有 `# NAME: openai`，没有既存规则可继承。
- 项目不存在相关 feature 文档，无需做 feature 与代码一致性校验。

## 规则依据

- OpenAI 官方网络建议列出的 ChatGPT Web/App 域名，以及 ChatGPT/Codex 的 WebSocket 目标。
- OpenAI 官方 `chatgpt-voice.json` 在 2026-03-26 生成的 23 个语音 IPv4 前缀。
- `openai.list` 仅保留核心服务、认证、上传、静态资源和 WebSocket 规则。
- `openai-extended.list` 放置客服、计费、遥测、iOS 诊断和 Voice UDP 规则，需与核心文件一起加载。
- 已删除当前官方清单不再列出的旧 Azure/Arkose/Cloudflare CDN、旧 Datadog、LiveKit 和旧静态资源端点；未采用 `DOMAIN-KEYWORD,openai` 或整段 ASN。

## 验证

- 两份规则的类型、字段数和域名/CIDR 格式校验通过。
- `openai.list`：8 条 `DOMAIN`、6 条 `DOMAIN-SUFFIX`，共 14 条。
- `openai-extended.list`：5 条 `DOMAIN`、2 条 `DOMAIN-SUFFIX`、23 条 `IP-CIDR`，共 30 条。
- 核心与扩展文件没有重复规则；当前官方清单的 28 个代表性端点全部命中。
- 23 条 Voice IPv4 `/32` 与 2026-07-20 获取的官方动态 JSON 完全一致，并带 `no-resolve`。
