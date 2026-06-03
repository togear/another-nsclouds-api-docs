# Google - Image Generations

### 1. Overview

Google's image generation API, compatible with OpenAI interface format.

{% hint style="success" %}
This API is compatible with OpenAI interface format.
{% endhint %}

**Model List:**

* `imagen-3.0-generate-001` (image_generation mode)
* `imagen-3.0-generate-002` (image_generation mode)
* `imagen-3.0-fast-generate-001` (image_generation mode)
* `gemini-2.5-flash-image` (image_generation mode)
* `gemini-3-pro-image-preview` (image_generation mode)
* `gemini-3.1-flash-image-preview` (image_generation mode)

### Functionality Verification

| Function | Status | Description |
|----------|--------|-------------|
| Basic Request | ✅ Verification Passed | Returns base64 image |
| Image Edit | ⏳ Pending | - |

### 2. API Details

{% openapi-operation spec="google-en-{{ENV}}" path="/v1/images/generations" method="post" %}
[OpenAPI Google](https://raw.githubusercontent.com/liujia-hbu/nsclouds-api-docs/main/docs/bundled/{{ENV}}/en/google.bundled.yaml)
{% endopenapi-operation %}