# 字节豆包(volcengine) - 文本补全

### 1. 概述

字节跳动推出的文本补全 API，与 OpenAI 接口格式兼容。

{% hint style="success" %}
本 API 与 OpenAI 接口格式兼容。
{% endhint %}

**模型列表：**

* `volcengine/doubao-seed-1-8-251228`
* `volcengine/doubao-seed-1-6-251015`
* `volcengine/doubao-seed-1-6-lite-251015`

### 2. 接口详情

{% openapi-operation spec="volcengine-zh-{{ENV}}" path="/v1/completions" method="post" %}
[OpenAPI volcengine](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/{{ENV}}/zh/volcengine.bundled.yaml)
{% endopenapi-operation %}
