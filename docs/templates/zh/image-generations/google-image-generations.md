# Google - 图像生成

### 1. 概述

Google 的图像生成 API，与 OpenAI 接口格式兼容。

{% hint style="success" %}
此 API 与 OpenAI 接口格式兼容。
{% endhint %}

**模型列表：**

* `imagen-3.0-generate-001` (image_generation 模式)
* `imagen-3.0-generate-002` (image_generation 模式)
* `imagen-3.0-fast-generate-001` (image_generation 模式)
* `gemini-2.5-flash-image` (image_generation 模式)
* `gemini-3-pro-image-preview` (image_generation 模式)
* `gemini-3.1-flash-image-preview` (image_generation 模式)

### 2. 接口详情

{% openapi-operation spec="google-zh-{{ENV}}" path="/v1/images/generations" method="post" %}
[OpenAPI Google](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/{{ENV}}/zh/google.bundled.yaml)
{% endopenapi-operation %}