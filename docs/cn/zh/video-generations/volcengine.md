# Volcengine - 视频生成

### 1. 概述

Volcengine 在当前环境中提供的视频生成能力。

{% hint style="success" %}
本接口提供与 OpenAI Videos 兼容的请求路径。不同厂家和模型的实际能力可能不同。
{% endhint %}

**模型列表：**

* `doubao-seedance-2-0-260128`
* `doubao-seedance-2-0-fast-260128`


### 2. 接口详情

{% openapi-operation spec="volcengine-zh-cn" path="/v1/videos" method="post" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/cn/zh/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-zh-cn" path="/v1/videos/{video_id}" method="get" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/cn/zh/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-zh-cn" path="/v1/videos/{video_id}/content" method="get" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/cn/zh/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-zh-cn" path="/v1/videos" method="get" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/cn/zh/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-zh-cn" path="/v1/videos/{video_id}" method="delete" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/cn/zh/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-zh-cn" path="/v1/videos/{video_id}/remix" method="post" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/cn/zh/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-zh-cn" path="/v1/videos/edits" method="post" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/cn/zh/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-zh-cn" path="/v1/videos/extensions" method="post" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/cn/zh/volcengine.bundled.yaml)
{% endopenapi-operation %}
