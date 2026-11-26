# proxy-rules

## Shadowrocket 加载顺序

在 Shadowrocket 中以 `RULE-SET` 加载下列文件。如果各产品使用不同策略，将产品规则放在共享 Google 规则之前。

| 用途 | 规则集 |
| --- | --- |
| OpenAI / ChatGPT | `openai.list`、`openai-extended.list` |
| Claude / Anthropic | `claude.list`、`claude-extended.list` |
| Gemini / Antigravity / NotebookLM | `gemini.list`、`gemini-extended.list` |
| Google 公共服务、Gemini API 和 Google One 订阅 | `google-shared.list`，只需加载一次 |

`DOMAIN-KEYWORD` 按主机名中的连续字符串匹配。例如，`gemini.google.com` 同时含有 `gemini` 和 `google`，先命中的规则决定出口。`generativelanguage.googleapis.com`、`one.google.com` 和 `payments.google.com` 由共享表的 `google` 匹配。希望 Gemini 对话、API 和订阅使用同一出口时，为 Gemini 两张表和共享表选择同一策略。

关键词也会匹配第三方主机名，例如 `google.example.org`。需要单独分流的域名，请将精确规则放在关键词规则之前。
