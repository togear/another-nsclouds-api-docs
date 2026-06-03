---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/x8h0Gte093KpUAW4Bcpp/audio-transcriptions/deepseek-audio-transcriptions
---

# DeepSeek

### 1. Overview

The audio transcription API launched by DeepSeek, compatible with OpenAI interface format.

{% hint style="success" %}
This API is compatible with OpenAI interface format.
{% endhint %}

**Model List:**

* `deepseek-audio-transcription`

### 2. API Details

{% openapi-operation spec="deepseek-en-{{ENV}}" path="/v1/audio/transcriptions" method="post" %}
[OpenAPI deepseek](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/{{ENV}}/en/deepseek.bundled.yaml)
{% endopenapi-operation %}
