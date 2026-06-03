# 深度求索(DeepSeek) - 文本补全

### 1. 概述

深度求索推出的文本补全 API，与 OpenAI 接口格式兼容。

{% hint style="success" %}
本 API 与 OpenAI 接口格式兼容。
{% endhint %}

**模型列表：**

* `volcengine/deepseek-v3-1-terminus`

### 2. 接口详情

{% openapi-operation spec="deepseek-zh-{{ENV}}" path="/v1/completions" method="post" %}
[OpenAPI deepseek](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/{{ENV}}/zh/deepseek.bundled.yaml)
{% endopenapi-operation %}
