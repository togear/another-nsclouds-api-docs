# OpenAI - 文本补全

### 1. 概述

OpenAI 的文本补全 API，与 OpenAI 接口格式兼容。

{% hint style="success" %}
本 API 与 OpenAI 接口格式兼容。
{% endhint %}

**模型列表：**

* `gpt-5` (chat 模式，支持 completion)
* `gpt-5.2` (chat 模式，支持 completion)
* `gpt-5.4` (chat 模式，支持 completion)
* `gpt-5.3-codex` (chat 模式，支持 completion)

### 2. 接口详情

{% openapi-operation spec="openai-zh-{{ENV}}" path="/v1/completions" method="post" %}
[OpenAPI openai](https://raw.githubusercontent.com/ngaa-dev/nsclouds-api-docs/main/docs/bundled/{{ENV}}/zh/openai.bundled.yaml)
{% endopenapi-operation %}
