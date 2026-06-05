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

列表接口只返回当前 `sk-` 密钥创建并已写入 `LiteLLM_VideoTaskTable` 的视频任务。网关不会调用或暴露 VolcEngine 上游全量任务列表；历史未写入索引的任务不会出现在列表中，但仍可使用创建时返回的 `video_id` 调用查询或内容下载接口获取状态和视频 URL。

生产环境需要完成 `LiteLLM_VideoTaskTable` 数据库迁移。数据库不可用时仅使用进程内临时缓存兜底，服务重启后会丢失任务与用户密钥的对应关系。

| 查询参数 | 本地索引行为 | 说明 |
| --- | --- | --- |
| `model` | 按 AILLM 索引里的公开模型名或模型 ID 过滤 | 推荐传入 `doubao-seedance-2-0-260128` 等公开模型名。 |
| `limit` / `page_size` | 本地分页大小 | 默认按服务端配置；最大 100。 |
| `page_num` | 本地页码 | 从 1 开始。 |
| `status` / `filter.status` | 本地状态过滤 | `succeeded` 会归一化为 `completed`，`running` 会归一化为 `in_progress`。 |
| `custom_llm_provider` | 刷新任务状态时的厂家提示 | 通常可由 `video_...` ID 自动解析；Seedance 使用 `volcengine`。 |
| `after` / `order` / `page_token` / `filter.model` | 兼容接收，不参与本地索引分页 | 请使用 `page_num`、`limit` 和 `model`。 |

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
