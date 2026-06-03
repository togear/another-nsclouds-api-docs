# Google - 文本补全

### 1. 概述

Google 的文本补全 API，与 OpenAI 接口格式兼容。

{% hint style="success" %}
本 API 与 OpenAI 接口格式兼容。
{% endhint %}

**模型列表：**

* `gemini-2.5-flash` (completion 模式)
* `gemini-2.5-pro` (completion 模式)
* `gemini-3-flash-preview` (completion 模式)
* `gemini-3-pro-preview` (completion 模式)

### 2. 接口详情

{% openapi-operation spec="google-zh-{{ENV}}" path="/v1/completions" method="post" %}
[OpenAPI Google](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/{{ENV}}/zh/google.bundled.yaml)
{% endopenapi-operation %}