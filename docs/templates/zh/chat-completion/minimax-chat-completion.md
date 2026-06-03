# MiniMax - 对话生成

### 1. 概述

MiniMax 的对话生成 API，与 OpenAI 接口格式兼容。

{% hint style="success" %}
此 API 与 OpenAI 接口格式兼容。
{% endhint %}

**模型列表：**

* `MiniMax-M2.5` (chat 模式)

### 2. 接口详情

{% openapi-operation spec="minimax-zh-{{ENV}}" path="/v1/chat/completions" method="post" %}
[OpenAPI MiniMax](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/{{ENV}}/zh/minimax.bundled.yaml)
{% endopenapi-operation %}
