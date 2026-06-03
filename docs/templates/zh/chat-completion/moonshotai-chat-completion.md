# Moonshot AI - 对话生成

### 1. 概述

Moonshot AI 的对话生成 API，与 OpenAI 接口格式兼容。

{% hint style="success" %}
此 API 与 OpenAI 接口格式兼容。
{% endhint %}

**模型列表：**

* `kimi-k2.5` (chat 模式)
* `kimi-k2-thinking` (chat 模式)

### 2. 接口详情

{% openapi-operation spec="moonshotai-zh-{{ENV}}" path="/v1/chat/completions" method="post" %}
[OpenAPI Moonshot AI](https://raw.githubusercontent.com/ngaa-dev/nsclouds-api-docs/main/docs/bundled/{{ENV}}/zh/moonshotai.bundled.yaml)
{% endopenapi-operation %}