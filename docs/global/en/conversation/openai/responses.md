# OpenAI - Responses

### 1. Overview

OpenAI's Responses protocol capability.

{% hint style="success" %}
This API is compatible with the Responses protocol.
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

Use `input_image` content parts with `gpt-5.4` when you need the model to inspect an image. The image can be a public URL or a base64 data URL.

```json
{
  "model": "gpt-5.4",
  "input": [
    {
      "role": "user",
      "content": [
        { "type": "input_text", "text": "Describe this image and extract any visible text." },
        {
          "type": "input_image",
          "image_url": "https://example.com/image.png",
          "detail": "high"
        }
      ]
    }
  ]
}
```

### 3. File Input

The `/v1/responses` endpoint supports file input with `input_file` content parts. You can reference a publicly accessible file URL directly with `file_url`.

```json
{
  "model": "gpt-5.4",
  "stream": true,
  "input": [
    {
      "role": "user",
      "content": [
        { "type": "input_text", "text": "Summarize this paper's core idea." },
        {
          "type": "input_file",
          "file_url": "https://arxiv.org/pdf/1706.03762v7"
        }
      ]
    }
  ]
}
```


### 4. API Details

{% openapi-operation spec="openai-en-global" path="/v1/responses" method="post" %}
[OpenAPI OpenAI](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/global/en/openai.bundled.yaml)
{% endopenapi-operation %}
