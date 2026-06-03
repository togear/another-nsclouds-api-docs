# Volcengine - Video Generations

### 1. Overview

Volcengine exposes video generation capabilities in this environment.

{% hint style="success" %}
This endpoint provides an OpenAI-compatible Videos path. Actual capabilities may vary by vendor and model.
{% endhint %}

**Supported models：**

* `doubao-seedance-2-0-260128`
* `doubao-seedance-2-0-fast-260128`


### 2. API Details

{% openapi-operation spec="volcengine-en-cn" path="/v1/videos" method="post" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/cn/en/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-en-cn" path="/v1/videos/{video_id}" method="get" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/cn/en/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-en-cn" path="/v1/videos/{video_id}/content" method="get" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/cn/en/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-en-cn" path="/v1/videos" method="get" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/cn/en/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-en-cn" path="/v1/videos/{video_id}" method="delete" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/cn/en/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-en-cn" path="/v1/videos/{video_id}/remix" method="post" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/cn/en/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-en-cn" path="/v1/videos/edits" method="post" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/cn/en/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-en-cn" path="/v1/videos/extensions" method="post" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/cn/en/volcengine.bundled.yaml)
{% endopenapi-operation %}
