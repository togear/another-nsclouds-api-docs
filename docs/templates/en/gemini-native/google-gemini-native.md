# Google - Gemini Native

### 1. Overview

Gemini native protocol APIs for `generateContent` and `streamGenerateContent`.

{% hint style="success" %}
This endpoint provides a Google Gemini native-compatible path.
{% endhint %}

### 2. API Details

{% openapi-operation spec="google-en-{{ENV}}" path="/v1beta/models/{model}:generateContent" method="post" %}
[OpenAPI google](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/{{ENV}}/en/google.bundled.yaml)
{% endopenapi-operation %}

{% openapi-operation spec="google-en-{{ENV}}" path="/v1beta/models/{model}:streamGenerateContent" method="post" %}
[OpenAPI google](https://raw.githubusercontent.com/togear/another-nsclouds-api-docs/main/docs/bundled/{{ENV}}/en/google.bundled.yaml)
{% endopenapi-operation %}
