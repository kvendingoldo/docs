---
editable: false
sourcePath: en/_api-ref-grpc/serverless/apigateway/v1/apigateway/api-ref/grpc/ApiGateway/removeDomain.md
---

# API Gateway Service, gRPC: ApiGatewayService.RemoveDomain {#RemoveDomain}

Detaches domain from the specified API gateway.

## gRPC request

**rpc RemoveDomain ([RemoveDomainRequest](#yandex.cloud.serverless.apigateway.v1.RemoveDomainRequest)) returns ([operation.Operation](#yandex.cloud.operation.Operation))**

## RemoveDomainRequest {#yandex.cloud.serverless.apigateway.v1.RemoveDomainRequest}

```json
{
  "apiGatewayId": "string",
  "domainId": "string"
}
```

#|
||Field | Description ||
|| apiGatewayId | **string**

Required field. ID of the API gateway from which the domain is being detached. ||
|| domainId | **string**

Required field. ID of the detaching domain. ||
|#

## operation.Operation {#yandex.cloud.operation.Operation}

```json
{
  "id": "string",
  "description": "string",
  "createdAt": "google.protobuf.Timestamp",
  "createdBy": "string",
  "modifiedAt": "google.protobuf.Timestamp",
  "done": "bool",
  "metadata": {
    "apiGatewayId": "string",
    "domainId": "string"
  },
  // Includes only one of the fields `error`, `response`
  "error": "google.rpc.Status",
  "response": "google.protobuf.Empty"
  // end of the list of possible fields
}
```

An Operation resource. For more information, see [Operation](/docs/api-design-guide/concepts/operation).

#|
||Field | Description ||
|| id | **string**

ID of the operation. ||
|| description | **string**

Description of the operation. 0-256 characters long. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp. ||
|| createdBy | **string**

ID of the user or service account who initiated the operation. ||
|| modifiedAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

The time when the Operation resource was last modified. ||
|| done | **bool**

If the value is `false`, it means the operation is still in progress.
If `true`, the operation is completed, and either `error` or `response` is available. ||
|| metadata | **[RemoveDomainMetadata](#yandex.cloud.serverless.apigateway.v1.RemoveDomainMetadata)**

Service-specific metadata associated with the operation.
It typically contains the ID of the target resource that the operation is performed on.
Any method that returns a long-running operation should document the metadata type, if any. ||
|| error | **[google.rpc.Status](https://cloud.google.com/tasks/docs/reference/rpc/google.rpc#status)**

The error result of the operation in case of failure or cancellation.

Includes only one of the fields `error`, `response`.

The operation result.
If `done == false` and there was no failure detected, neither `error` nor `response` is set.
If `done == false` and there was a failure detected, `error` is set.
If `done == true`, exactly one of `error` or `response` is set. ||
|| response | **[google.protobuf.Empty](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#google.protobuf.Empty)**

The normal response of the operation in case of success.
If the original method returns no data on success, such as Delete,
the response is [google.protobuf.Empty](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#google.protobuf.Empty).
If the original method is the standard Create/Update,
the response should be the target resource of the operation.
Any method that returns a long-running operation should document the response type, if any.

Includes only one of the fields `error`, `response`.

The operation result.
If `done == false` and there was no failure detected, neither `error` nor `response` is set.
If `done == false` and there was a failure detected, `error` is set.
If `done == true`, exactly one of `error` or `response` is set. ||
|#

## RemoveDomainMetadata {#yandex.cloud.serverless.apigateway.v1.RemoveDomainMetadata}

#|
||Field | Description ||
|| apiGatewayId | **string**

ID of the API gateway from which the domain is being detached. ||
|| domainId | **string**

ID of the detaching domain. ||
|#