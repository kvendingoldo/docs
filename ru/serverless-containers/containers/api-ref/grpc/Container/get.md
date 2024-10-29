---
editable: false
sourcePath: en/_api-ref-grpc/serverless/containers/v1/containers/api-ref/grpc/Container/get.md
---

# Serverless Containers Service, gRPC: ContainerService.Get {#Get}

Returns the specified container.

To get the list of all available containers, make a [List](/docs/serverless/containers/api-ref/grpc/Container/list#List) request.

## gRPC request

**rpc Get ([GetContainerRequest](#yandex.cloud.serverless.containers.v1.GetContainerRequest)) returns ([Container](#yandex.cloud.serverless.containers.v1.Container))**

## GetContainerRequest {#yandex.cloud.serverless.containers.v1.GetContainerRequest}

```json
{
  "containerId": "string"
}
```

#|
||Field | Description ||
|| containerId | **string**

Required field. ID of the container to return.

To get a container ID make a [ContainerService.List](/docs/serverless/containers/api-ref/grpc/Container/list#List) request. ||
|#

## Container {#yandex.cloud.serverless.containers.v1.Container}

```json
{
  "id": "string",
  "folderId": "string",
  "createdAt": "google.protobuf.Timestamp",
  "name": "string",
  "description": "string",
  "labels": "string",
  "url": "string",
  "status": "Status"
}
```

#|
||Field | Description ||
|| id | **string**

ID of the container. Generated at creation time. ||
|| folderId | **string**

ID of the folder that the container belongs to. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp for the container. ||
|| name | **string**

Name of the container. The name is unique within the folder. ||
|| description | **string**

Description of the container. ||
|| labels | **string**

Container labels as `key:value` pairs. ||
|| url | **string**

URL that needs to be requested to call the container. ||
|| status | enum **Status**

Status of the container.

- `STATUS_UNSPECIFIED`
- `CREATING`: Container is being created.
- `ACTIVE`: Container is ready for use.
- `DELETING`: Container is being deleted.
- `ERROR`: Container failed. The only allowed action is delete. ||
|#