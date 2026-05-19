# OpenAI - Chat Completions

### 1. Overview

OpenAI's conversation API capability.

{% hint style="success" %}
This API is compatible with the OpenAI Chat Completions interface.
{% endhint %}

**Supported models：**

* `gpt-5`
* `gpt-5.1`
* `gpt-5.2`
* `gpt-5.3-codex`
* `gpt-5.4`
* `gpt-5.4-mini`
* `gpt-5.5`


### 2. Image Input (Multimodal)

The `/v1/chat/completions` endpoint supports image input with `image_url` content parts. For file input, use the `/v1/responses` endpoint instead.

```json
{
  "model": "gpt-5.4",
  "messages": [
    {
      "role": "user",
      "content": [
        { "type": "text", "text": "What is in this image?" },
        {
          "type": "image_url",
          "image_url": {
            "url": "https://example.com/image.png"
          }
        }
      ]
    }
  ],
  "max_completion_tokens": 300
}
```

### 3. API Details

{% openapi-operation spec="openai-en-global" path="/v1/chat/completions" method="post" %}
[OpenAPI OpenAI](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/global/en/openai.bundled.yaml)
{% endopenapi-operation %}
