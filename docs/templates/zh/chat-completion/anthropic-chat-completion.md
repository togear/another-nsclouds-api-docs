# Anthropic - 对话生成

### 1. 概述

Anthropic 的对话生成 API，与 OpenAI 接口格式兼容。

{% hint style="success" %}
本 API 与 OpenAI 接口格式兼容。
{% endhint %}

**模型列表：**

* `claude-haiku-4.5` (chat 模式)
* `claude-opus-4.5` (chat 模式)
* `claude-sonnet-4.5` (chat 模式)
* `claude-opus-4.6` (chat 模式)
* `claude-sonnet-4.6` (chat 模式)

### 2. 接口详情

{% openapi-operation spec="anthropic-zh-{{ENV}}" path="/v1/chat/completions" method="post" %}
[OpenAPI Anthropic](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/{{ENV}}/zh/anthropic.bundled.yaml)
{% endopenapi-operation %}