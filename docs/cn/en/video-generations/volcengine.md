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

The list endpoint returns only video tasks created by the current `sk-` key and recorded in `LiteLLM_VideoTaskTable`. The gateway does not call or expose the provider's full VolcEngine task list. Historical tasks that were not indexed do not appear in the list, but callers can still use the `video_id` returned at creation time with the retrieve or content endpoints to get task status and the video URL.

Production deployments should run the `LiteLLM_VideoTaskTable` database migration. If the database is unavailable, the gateway falls back to in-process cache only, so task-to-key mappings are lost after a process restart.

| Query parameter | Local index behavior | Notes |
| --- | --- | --- |
| `model` | Filters by the public model name or model ID in the AILLM index | Prefer public names such as `doubao-seedance-2-0-260128`. |
| `limit` / `page_size` | Local page size | Defaults to the service configuration; maximum 100. |
| `page_num` | Local page number | Starts from 1. |
| `status` / `filter.status` | Local status filter | `succeeded` is normalized to `completed`; `running` is normalized to `in_progress`. |
| `custom_llm_provider` | Provider hint when refreshing task status | Usually inferred from the `video_...` ID; use `volcengine` for Seedance. |
| `after` / `order` / `page_token` / `filter.model` | Accepted for compatibility, not used for local index pagination | Use `page_num`, `limit`, and `model` instead. |

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
