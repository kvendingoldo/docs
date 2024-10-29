---
editable: false
sourcePath: en/_api-ref-grpc/mdb/redis/v1/api-ref/grpc/Cluster/updateHosts.md
---

# Managed Service for Redis API, gRPC: ClusterService.UpdateHosts {#UpdateHosts}

Updates the specified hosts.

## gRPC request

**rpc UpdateHosts ([UpdateClusterHostsRequest](#yandex.cloud.mdb.redis.v1.UpdateClusterHostsRequest)) returns ([operation.Operation](#yandex.cloud.operation.Operation))**

## UpdateClusterHostsRequest {#yandex.cloud.mdb.redis.v1.UpdateClusterHostsRequest}

```json
{
  "clusterId": "string",
  "updateHostSpecs": [
    {
      "hostName": "string",
      "replicaPriority": "google.protobuf.Int64Value",
      "assignPublicIp": "bool",
      "updateMask": "google.protobuf.FieldMask"
    }
  ]
}
```

#|
||Field | Description ||
|| clusterId | **string**

Required field. ID of the Redis cluster to update hosts in.
To get the Redis cluster ID, use a [ClusterService.List](/docs/managed-redis/api-ref/grpc/Cluster/list#List) request. ||
|| updateHostSpecs[] | **[UpdateHostSpec](#yandex.cloud.mdb.redis.v1.UpdateHostSpec)**

New configurations to apply to hosts. ||
|#

## UpdateHostSpec {#yandex.cloud.mdb.redis.v1.UpdateHostSpec}

#|
||Field | Description ||
|| hostName | **string**

Required field. Name of the host to update.
To get the Redis host name, use a [ClusterService.ListHosts](/docs/managed-redis/api-ref/grpc/Cluster/listHosts#ListHosts) request. ||
|| replicaPriority | **[google.protobuf.Int64Value](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/int64-value)**

A replica with a low priority number is considered better for promotion.
A replica with priority of 0 will never be selected by Redis Sentinel for promotion.
Works only for non-sharded clusters. Default value is 100. ||
|| assignPublicIp | **bool**

Whether the host should get a public IP address on update. ||
|| updateMask | **[google.protobuf.FieldMask](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/field-mask)**

Field mask that specifies which fields of the Redis host should be updated. ||
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
    "clusterId": "string",
    "hostNames": [
      "string"
    ]
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
|| metadata | **[UpdateClusterHostsMetadata](#yandex.cloud.mdb.redis.v1.UpdateClusterHostsMetadata)**

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

## UpdateClusterHostsMetadata {#yandex.cloud.mdb.redis.v1.UpdateClusterHostsMetadata}

#|
||Field | Description ||
|| clusterId | **string**

ID of the Redis cluster to update hosts in. ||
|| hostNames[] | **string**

Names of hosts that are being updated. ||
|#