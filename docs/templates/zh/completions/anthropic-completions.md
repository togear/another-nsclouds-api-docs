# Anthropic - 文本补全

### 1. 概述

Anthropic 的文本补全 API，与 OpenAI 接口格式兼容。

{% hint style="success" %}
本 API 与 OpenAI 接口格式兼容。
{% endhint %}

**模型列表：**

* `claude-haiku-4.5` (completion 模式)
* `claude-opus-4.5` (completion 模式)
* `claude-sonnet-4.5` (completion 模式)
* `claude-opus-4.6` (completion 模式)
* `claude-sonnet-4.6` (completion 模式)

### 2. 接口详情

{% openapi-operation spec="anthropic-zh-{{ENV}}" path="/v1/completions" method="post" %}
[OpenAPI Anthropic](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/{{ENV}}/zh/anthropic.bundled.yaml)
{% endopenapi-operation %}