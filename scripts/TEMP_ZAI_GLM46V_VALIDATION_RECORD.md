# ZAI GLM-4.6V 与 GitBook 多模态用例验证记录

记录日期：2026-05-27

## 验证边界

- `zai` 的 `max_completion_tokens` 适配只验证本地 `http://127.0.0.1:5000`，因为线上还没有升级最新代码。
- GitBook 当前展示的其他请求用例仍验证线上 `https://aillm.nscloud.ai`。
- API Key 只通过本机环境变量读取，记录中不写入密钥。

## 本地 ZAI 验证

已通过：

- `POST /v1/chat/completions`，`model=glm-4.6v`，非流式，带 `max_completion_tokens`：通过。
- `POST /v1/chat/completions`，`model=zai/glm-4.6v`，非流式，带 `max_completion_tokens`：通过。
- `POST /v1/chat/completions`，`model=glm-4.6v`，流式，带 `max_completion_tokens`：通过，返回 SSE 且以 `[DONE]` 结束。

结论：

- 本地最新 `aillm` 已能接受 OpenAI 风格的 `max_completion_tokens`。
- 该参数应在 ZAI 适配层转为智谱实际支持的 `max_tokens`，不要继续向 ZAI 后端透传 `max_completion_tokens`。

## 线上 GitBook 用例验证

已通过：

- Chat Completions `image_url` 公网 URL：通过，`model=gpt-5.4`。
- Chat Completions `image_url` data URL：通过，`model=gpt-5.4`。
- Chat Completions `file_data` PDF data URL：通过，`model=gpt-5`。
- Responses `input_image.image_url` 公网 URL：通过，`model=gpt-5.4`。
- Responses `input_image.image_url` data URL：通过，`model=gpt-5.4`。
- Responses `input_file.file_url` PDF URL：通过，`model=gpt-5`。
- Responses `input_file.file_data` PDF data URL：通过，`model=gpt-5`。

已失败/不作为展示用例：

- Chat Completions `file_data` 使用 `data:text/plain;base64,...`：失败，线上返回 `The request is invalid.`。
- Responses `input_file.file_data` 使用 `data:text/plain;base64,...`：失败，线上返回 `The request is invalid.`。
- 假 `file_id` 示例不是真实 Files API 返回值，不应作为可复制运行用例展示。

## 文档展示建议

- `file_id` 字段保留在 schema 和说明中，备注为“建设中/适配中”，说明其来源必须是 Files API 上传后返回的真实 ID。
- 可复制 request examples 中不放假 `file_id`。
- `file_data` 示例使用已验证通过的完整 PDF data URL，不使用带省略号的占位字符串。
