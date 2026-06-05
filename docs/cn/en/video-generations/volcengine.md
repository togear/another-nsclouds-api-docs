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
`/v1/videos` keeps an OpenAI-compatible Videos path externally and maps requests to Ark Seedance task APIs upstream. Media convenience parameters only support URLs or uploaded `asset://...` references; local file objects, BytesIO values, and multipart UploadFile payloads are not uploaded automatically.
{% endhint %}

#### Task List Query

| Query parameter | VolcEngine parameter | Notes |
| --- | --- | --- |
| `model` | `filter.model` | Used for Router selection and also converted to the provider-side model filter. Router aliases are normalized to the actual VolcEngine model id. |
| `filter.model` | `filter.model` | Explicit model filter; takes precedence over `model`. |
| `limit` | `page_size` | Page size. |
| `page_num` | `page_num` | Recommended VolcEngine page-number pagination parameter. |
| `after` | `page_num` | Mapped only when the decoded value is a positive integer; prefer `page_num`. |
| `status` / `filter.status` | `filter.status` | `completed` maps to `succeeded`; `in_progress` maps to `running`. |
| `order` / `page_token` | Not forwarded | VolcEngine list does not use OpenAI-style ordering or page tokens. |

#### Media Inputs

- `input_reference`, `image`, `video`, and `audio` support URL strings, uploaded `asset://...` references, or objects containing `url`, `image_url.url`, `video_url.url`, or `audio_url.url`.
- Upload local files to an accessible asset endpoint first, then pass the URL or `asset://...` reference.
- `extra_body.content` is passed through as native VolcEngine content; callers must ensure media URLs meet upstream requirements.

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
