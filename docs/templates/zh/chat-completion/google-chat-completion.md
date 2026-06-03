# Google - 对话生成

### 1. 概述

Google 的对话生成 API，与 OpenAI 接口格式兼容。

{% hint style="success" %}
本 API 与 OpenAI 接口格式兼容。
{% endhint %}
    
**模型列表：**

* `gemini-2.5-flash` (chat 模式)
* `gemini-2.5-pro` (chat 模式)
* `gemini-3-flash-preview` (chat 模式)
* `gemini-3-pro-preview` (chat 模式)

### 2. 接口详情

{% openapi-operation spec="google-zh-{{ENV}}" path="/v1/chat/completions" method="post" %}
[OpenAPI Google](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/{{ENV}}/zh/google.bundled.yaml)
{% endopenapi-operation %}