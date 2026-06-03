# 深度求索(DeepSeek)

### 1. 概述

深度求索推出的当前最实惠的国产大模型，提示/生成费用较低，非常适合用于翻译需求。

{% hint style="success" %}
本 API 与 OpenAI 接口格式兼容。
{% endhint %}

**模型列表：**

* `deepseek-v3.1`
* `deepseek-v3.2`

### 2.接口详情

{% openapi-operation spec="deepseek-zh-{{ENV}}" path="/v1/chat/completions" method="post" %}
[OpenAPI deepseek](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/{{ENV}}/zh/deepseek.bundled.yaml)
{% endopenapi-operation %}
