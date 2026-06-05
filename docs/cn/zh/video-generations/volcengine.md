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
`/v1/videos` 提供 OpenAI-compatible Videos 路径。媒体参数支持 URL 或 `asset://...` 已上传资产引用；本地文件需要先上传后再传入 URL 或资产引用。
{% endhint %}

#### 任务列表查询

列表接口只返回当前 API key 下的视频任务，可按模型、状态和页码过滤。已有 `video_id` 时，也可以直接调用查询或内容下载接口获取状态和视频 URL。

| 查询参数 | 说明 |
| --- | --- |
| `model` | 按模型过滤。 |
| `status` / `filter.status` | 按状态过滤，例如 `completed`、`in_progress`。 |
| `limit` / `page_size` | 每页数量，最大 100。 |
| `page_num` | 页码，从 1 开始。 |

#### 媒体输入

- `input_reference`、`image`、`video`、`audio` 支持 URL 字符串、`asset://...` 已上传资产引用，或包含 URL 字段的对象。
- 本地文件需要先上传到可访问的资产端点，再把 URL 或 `asset://...` 传给接口。

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
