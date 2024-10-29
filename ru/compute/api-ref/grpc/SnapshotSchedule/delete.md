---
editable: false
sourcePath: en/_api-ref-grpc/compute/v1/api-ref/grpc/SnapshotSchedule/delete.md
---

# Compute Cloud API, gRPC: SnapshotScheduleService.Delete {#Delete}

Deletes the specified snapshot schedule.

Deleting a snapshot schedule removes its data permanently and is irreversible. However, deleting a schedule
does not delete any snapshots created by the schedule. You must delete snapshots separately.

The schedule is deleted only after all snapshot creations and deletions triggered by the schedule are completed.

## gRPC request

**rpc Delete ([DeleteSnapshotScheduleRequest](#yandex.cloud.compute.v1.DeleteSnapshotScheduleRequest)) returns ([operation.Operation](#yandex.cloud.operation.Operation))**

## DeleteSnapshotScheduleRequest {#yandex.cloud.compute.v1.DeleteSnapshotScheduleRequest}

```json
{
  "snapshotScheduleId": "string"
}
```

#|
||Field | Description ||
|| snapshotScheduleId | **string**

ID of the snapshot schedule to delete.

To get a snapshot schedule ID, make a [SnapshotScheduleService.List](/docs/compute/api-ref/grpc/SnapshotSchedule/list#List) request. ||
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
    "snapshotScheduleId": "string"
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
|| metadata | **[DeleteSnapshotScheduleMetadata](#yandex.cloud.compute.v1.DeleteSnapshotScheduleMetadata)**

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

## DeleteSnapshotScheduleMetadata {#yandex.cloud.compute.v1.DeleteSnapshotScheduleMetadata}

#|
||Field | Description ||
|| snapshotScheduleId | **string**

ID of the snapshot schedule that is being deleted. ||
|#