# MiniMax - Chat Completion

### 1. Overview

MiniMax's chat completion API, compatible with OpenAI interface format.

{% hint style="success" %}
This API is compatible with OpenAI interface format.
{% endhint %}

**Model List:**

* `MiniMax-M2.5` (chat mode)

### Functionality Verification

| Function | Status | Description |
|----------|--------|-------------|
| Basic Request | ✅ Verified | - |
| Streaming Response | ✅ Verified | Supports reasoning_content |
| Image Input | ❌ Not Supported | Model cannot recognize image input |
| Function Call | ⏳ Pending | - |

### 2. API Details

{% openapi-operation spec="minimax-en-{{ENV}}" path="/v1/chat/completions" method="post" %}
[OpenAPI MiniMax](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/{{ENV}}/en/minimax.bundled.yaml)
{% endopenapi-operation %}
