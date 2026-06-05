# Volcengine - Video Generations

### 1. Overview

Volcengine exposes video generation capabilities in this environment.

{% hint style="success" %}
This endpoint provides an OpenAI-compatible Videos path. Actual capabilities may vary by vendor and model.
{% endhint %}

**Supported models：**

* `doubao-seedance-2-0-260128`
* `doubao-seedance-2-0-fast-260128`


### 2. Seedance Parameter Notes

{% hint style="info" %}
`/v1/videos` provides an OpenAI-compatible Videos path. Media parameters support URLs or uploaded `asset://...` references; upload local files first, then pass the URL or asset reference.
{% endhint %}

#### Task List Query

The list endpoint returns only video tasks under the current API key. You can filter by model and status, and paginate by page number. If you already have a `video_id`, you can also call the retrieve or content endpoint directly to get task status and the video URL.

| Query parameter | Notes |
| --- | --- |
| `model` | Filter by model. |
| `status` / `filter.status` | Filter by status, such as `completed` or `in_progress`. |
| `limit` / `page_size` | Page size, up to 100. |
| `page_num` | Page number, starting from 1. |

#### Media Inputs

- `input_reference`, `image`, `video`, and `audio` support URL strings, uploaded `asset://...` references, or objects containing a URL field.
- Upload local files to an accessible asset endpoint first, then pass the URL or `asset://...` reference.

### 3. API Details

{% openapi-operation spec="volcengine-en-cn" path="/v1/videos" method="post" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/cn/en/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-en-cn" path="/v1/videos/{video_id}" method="get" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/cn/en/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-en-cn" path="/v1/videos/{video_id}/content" method="get" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/cn/en/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-en-cn" path="/v1/videos" method="get" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/cn/en/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-en-cn" path="/v1/videos/{video_id}" method="delete" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/cn/en/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-en-cn" path="/v1/videos/{video_id}/remix" method="post" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/cn/en/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-en-cn" path="/v1/videos/edits" method="post" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/cn/en/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-en-cn" path="/v1/videos/extensions" method="post" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/cn/en/volcengine.bundled.yaml)
{% endopenapi-operation %}
