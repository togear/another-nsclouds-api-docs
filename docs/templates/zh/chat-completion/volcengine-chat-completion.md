# 字节豆包(volcengine)

### 1. 概述

字节跳动推出的智能对话大模型，支持多模态交互、函数调用等高级功能。

{% hint style="success" %}
本 API 与 OpenAI 接口格式兼容。
{% endhint %}

**模型列表：**

* `volcengine/doubao-seed-1-8-251228`（推荐，支持多模态、函数调用）
* `volcengine/doubao-seed-1-6-251015`
* `volcengine/doubao-seed-1-6-lite-251015`

### 2.接口详情

{% openapi-operation spec="volcengine-zh-{{ENV}}" path="/v1/chat/completions" method="post" %}
[OpenAPI volcengine](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/{{ENV}}/zh/volcengine.bundled.yaml)
{% endopenapi-operation %}
