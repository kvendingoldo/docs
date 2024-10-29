---
editable: false
sourcePath: en/_api-ref-grpc/iam/v1/api-ref/grpc/ApiKey/get.md
---

# Identity and Access Management API, gRPC: ApiKeyService.Get {#Get}

Returns the specified API key.

To get the list of available API keys, make a [List](/docs/iam/api-ref/grpc/ApiKey/list#List) request.

## gRPC request

**rpc Get ([GetApiKeyRequest](#yandex.cloud.iam.v1.GetApiKeyRequest)) returns ([ApiKey](#yandex.cloud.iam.v1.ApiKey))**

## GetApiKeyRequest {#yandex.cloud.iam.v1.GetApiKeyRequest}

```json
{
  "apiKeyId": "string"
}
```

#|
||Field | Description ||
|| apiKeyId | **string**

Required field. ID of the API key to return.
To get the API key ID, use a [ApiKeyService.List](/docs/iam/api-ref/grpc/ApiKey/list#List) request. ||
|#

## ApiKey {#yandex.cloud.iam.v1.ApiKey}

```json
{
  "id": "string",
  "serviceAccountId": "string",
  "createdAt": "google.protobuf.Timestamp",
  "description": "string",
  "lastUsedAt": "google.protobuf.Timestamp",
  "scope": "string",
  "expiresAt": "google.protobuf.Timestamp"
}
```

An ApiKey resource. For more information, see [Api-Key](/docs/iam/concepts/authorization/api-key).

#|
||Field | Description ||
|| id | **string**

ID of the API Key. ||
|| serviceAccountId | **string**

ID of the service account that the API key belongs to. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp. ||
|| description | **string**

Description of the API key. 0-256 characters long. ||
|| lastUsedAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Timestamp for the last authentication using this API key. ||
|| scope | **string**

Scope of the API key. 0-256 characters long. ||
|| expiresAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

API key expiration timestamp. ||
|#