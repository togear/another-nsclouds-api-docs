---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/x8h0Gte093KpUAW4Bcpp/image-generations/openai-image-generations
---

# OpenAI

### 1. Overview

OpenAI's image generation API, compatible with OpenAI interface format.

{% hint style="success" %}
This API is compatible with OpenAI interface format.
{% endhint %}

**Model List:**

* `gpt-image-1` (image_generation mode)

### 2. API Details

{% openapi-operation spec="openai-en-{{ENV}}" path="/v1/images/generations" method="post" %}
[OpenAPI openai](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/{{ENV}}/en/openai.bundled.yaml)
{% endopenapi-operation %}
