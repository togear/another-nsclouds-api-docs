# Volcengine - 视频生成

### 1. 概述

Volcengine 在当前环境中提供的视频生成能力。

{% hint style="success" %}
本接口提供与 OpenAI Videos 兼容的请求路径。不同厂家和模型的实际能力可能不同。
{% endhint %}

**模型列表：**

* `doubao-seedance-2-0-260128`
* `doubao-seedance-2-0-fast-260128`


### 2. Seedance 参数说明

{% hint style="info" %}
`/v1/videos` 对外保留 OpenAI-compatible Videos 路径；发往 VolcEngine 时会映射为 Ark Seedance 任务接口。媒体 convenience 参数只支持 URL 或 `asset://...` 已上传资产引用，不支持本地文件对象、BytesIO 或 multipart UploadFile 自动转存。
{% endhint %}

#### 任务列表查询

| 查询参数 | VolcEngine 参数 | 说明 |
| --- | --- | --- |
| `model` | `filter.model` | 既用于 Router 选路，也会转成供应商侧模型过滤条件。使用模型别名时会归一化为实际 VolcEngine model id。 |
| `filter.model` | `filter.model` | 显式模型过滤条件；优先于 `model`。 |
| `limit` | `page_size` | 每页数量。 |
| `page_num` | `page_num` | VolcEngine 推荐页码分页参数。 |
| `after` | `page_num` | 仅当解码后是正整数时映射为页码；推荐直接使用 `page_num`。 |
| `status` / `filter.status` | `filter.status` | `completed` 映射为 `succeeded`，`in_progress` 映射为 `running`。 |
| `order` / `page_token` | 不透传 | VolcEngine list 不使用 OpenAI-style 排序和 page token。 |

#### 媒体输入

- `input_reference`、`image`、`video`、`audio` 支持 URL 字符串、`asset://...` 已上传资产引用，或包含 `url` / `image_url.url` / `video_url.url` / `audio_url.url` 的对象。
- 本地文件需要先上传到可访问的资产端点，再把 URL 或 `asset://...` 传给接口。
- `extra_body.content` 会作为 VolcEngine 原生 content 透传，调用方需自行保证媒体地址符合上游要求。

### 3. 接口详情

{% openapi-operation spec="volcengine-zh-cn" path="/v1/videos" method="post" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/cn/zh/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-zh-cn" path="/v1/videos/{video_id}" method="get" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/cn/zh/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-zh-cn" path="/v1/videos/{video_id}/content" method="get" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/cn/zh/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-zh-cn" path="/v1/videos" method="get" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/cn/zh/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-zh-cn" path="/v1/videos/{video_id}" method="delete" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/cn/zh/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-zh-cn" path="/v1/videos/{video_id}/remix" method="post" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/cn/zh/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-zh-cn" path="/v1/videos/edits" method="post" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/cn/zh/volcengine.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="volcengine-zh-cn" path="/v1/videos/extensions" method="post" %}
[OpenAPI Volcengine](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/cn/zh/volcengine.bundled.yaml)
{% endopenapi-operation %}
