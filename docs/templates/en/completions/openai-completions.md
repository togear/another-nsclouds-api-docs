---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/x8h0Gte093KpUAW4Bcpp/completions/openai-completions
---

# OpenAI

### 1. Overview

OpenAI's text completion API, compatible with OpenAI interface format.

{% hint style="success" %}
This API is compatible with OpenAI interface format.
{% endhint %}

**Model List:**

* `gpt-5` (chat mode, supports completion)
* `gpt-5.2` (chat mode, supports completion)

### 2. API Details

{% openapi-operation spec="openai-en-{{ENV}}" path="/v1/completions" method="post" %}
[OpenAPI openai](https://raw.githubusercontent.com/ngaa-dev/nsclouds-api-docs/main/docs/bundled/{{ENV}}/en/openai.bundled.yaml)
{% endopenapi-operation %}
