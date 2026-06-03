# 字节豆包(volcengine) - 图像生成

### 1. 概述

字节跳动推出的图像生成 API，与 OpenAI 接口格式兼容。

{% hint style="success" %}
本 API 与 OpenAI 接口格式兼容。
{% endhint %}

**模型列表：**

* `volcengine/doubao-seedream-4-5-251128`
* `volcengine/doubao-seedream-4-0-250828`

### 2. 接口详情

{% openapi-operation spec="volcengine-zh-{{ENV}}" path="/v1/images/generations" method="post" %}
[OpenAPI volcengine](https://raw.githubusercontent.com/ngaa-dev/nsclouds-api-docs/main/docs/bundled/{{ENV}}/zh/volcengine.bundled.yaml)
{% endopenapi-operation %}
