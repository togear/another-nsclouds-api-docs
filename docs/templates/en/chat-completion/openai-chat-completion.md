---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/x8h0Gte093KpUAW4Bcpp/chat-completion/openai-chat-completion
---

# OpenAI

### 1. Overview

OpenAI is a world-leading AI research organization that provides powerful GPT series large language models, including GPT-4, GPT-3.5, etc., supporting various AI capabilities such as text generation, dialogue, and image generation.

{% hint style="success" %}
This API is compatible with OpenAI interface format.
{% endhint %}

**Model List:**

* `gpt-5` (chat mode)
* `gpt-5.1` (chat mode)
* `gpt-5.2` (chat mode)
* `gpt-5.4` (chat mode)
* `gpt-5.3-codex` (chat mode)

### 2. API Details

{% openapi-operation spec="openai-en-{{ENV}}" path="/v1/chat/completions" method="post" %}
[OpenAPI openai](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/{{ENV}}/en/openai.bundled.yaml)
{% endopenapi-operation %}
