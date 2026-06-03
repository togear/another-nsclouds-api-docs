---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/x8h0Gte093KpUAW4Bcpp/completions/deepseek-completions
---

# DeepSeek

### 1. Overview

The text completion API launched by DeepSeek, compatible with OpenAI interface format.

{% hint style="success" %}
This API is compatible with OpenAI interface format.
{% endhint %}

**Model List:**

* `deepseek-v3-1-terminus`

### 2. API Details

{% openapi-operation spec="deepseek-en-{{ENV}}" path="/v1/completions" method="post" %}
[OpenAPI deepseek](https://raw.githubusercontent.com/ngaa-dev/nsclouds-api-docs/main/docs/bundled/{{ENV}}/en/deepseek.bundled.yaml)
{% endopenapi-operation %}
