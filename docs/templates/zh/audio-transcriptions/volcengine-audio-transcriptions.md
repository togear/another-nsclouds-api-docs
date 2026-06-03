# 字节豆包(volcengine) - 音频转录

### 1. 概述

字节跳动推出的音频转录 API，与 OpenAI 接口格式兼容。

{% hint style="success" %}
本 API 与 OpenAI 接口格式兼容。
{% endhint %}

**模型列表：**

* `volcengine/doubao-asr-flash-1-6-251015`

### 2. 接口详情

{% openapi-operation spec="volcengine-zh-{{ENV}}" path="/v1/audio/transcriptions" method="post" %}
[OpenAPI volcengine](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/{{ENV}}/zh/volcengine.bundled.yaml)
{% endopenapi-operation %}
