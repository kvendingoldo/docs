---
editable: false
sourcePath: en/_api-ref-grpc/logging/v1/api-ref/grpc/LogGroup/list.md
---

# Cloud Logging Service, gRPC: LogGroupService.List {#List}

Retrieves the list of log groups in the specified folder.

## gRPC request

**rpc List ([ListLogGroupsRequest](#yandex.cloud.logging.v1.ListLogGroupsRequest)) returns ([ListLogGroupsResponse](#yandex.cloud.logging.v1.ListLogGroupsResponse))**

## ListLogGroupsRequest {#yandex.cloud.logging.v1.ListLogGroupsRequest}

```json
{
  "folderId": "string",
  "pageSize": "int64",
  "pageToken": "string",
  "filter": "string"
}
```

#|
||Field | Description ||
|| folderId | **string**

Required field. Folder ID of the log groups to return.

To get a folder ID make a [yandex.cloud.resourcemanager.v1.FolderService.List](/docs/resource-manager/api-ref/grpc/Folder/list#List) request. ||
|| pageSize | **int64**

The maximum number of results per page to return. If the number of available
results is larger than `page_size`, the service returns a [ListLogGroupsResponse.nextPageToken](#yandex.cloud.logging.v1.ListLogGroupsResponse)
that can be used to get the next page of results in subsequent list requests.

Default value: 100. ||
|| pageToken | **string**

Page token. To get the next page of results, set `page_token` to the
[ListLogGroupsResponse.nextPageToken](#yandex.cloud.logging.v1.ListLogGroupsResponse) returned by a previous list request. ||
|| filter | **string**

A filter expression that filters log groups listed in the response.

The expression must specify:
1. The field name. Currently filtering can only be applied to the [LogGroup.name](#yandex.cloud.logging.v1.LogGroup) field.
2. An `=` operator.
3. The value in double quotes (`"`). Must be 3-63 characters long and match the regular expression `[a-z][-a-z0-9]{1,61}[a-z0-9]`.
Example of a filter: `name=my-log-group`. ||
|#

## ListLogGroupsResponse {#yandex.cloud.logging.v1.ListLogGroupsResponse}

```json
{
  "groups": [
    {
      "id": "string",
      "folderId": "string",
      "cloudId": "string",
      "createdAt": "google.protobuf.Timestamp",
      "name": "string",
      "description": "string",
      "labels": "string",
      "status": "Status",
      "retentionPeriod": "google.protobuf.Duration",
      "dataStream": "string"
    }
  ],
  "nextPageToken": "string"
}
```

#|
||Field | Description ||
|| groups[] | **[LogGroup](#yandex.cloud.logging.v1.LogGroup)**

List of log groups in the specified folder. ||
|| nextPageToken | **string**

Token for getting the next page of the list. If the number of results is greater than
the specified [ListLogGroupsRequest.pageSize](#yandex.cloud.logging.v1.ListLogGroupsRequest), use `next_page_token` as the value
for the [ListLogGroupsRequest.pageToken](#yandex.cloud.logging.v1.ListLogGroupsRequest) parameter in the next list request.

Each subsequent page will have its own `next_page_token` to continue paging through the results. ||
|#

## LogGroup {#yandex.cloud.logging.v1.LogGroup}

#|
||Field | Description ||
|| id | **string**

Log group ID. ||
|| folderId | **string**

Log group folder ID. ||
|| cloudId | **string**

Log group cloud ID. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Log group creation time. ||
|| name | **string**

Log group name. ||
|| description | **string**

Log group description. ||
|| labels | **string**

Log group labels. ||
|| status | enum **Status**

Status of the log group.

- `STATUS_UNSPECIFIED`: Unknown status.

  Should never occur.
- `CREATING`: Log group is creating.
- `ACTIVE`: Log group is ready to accept messages,
- `DELETING`: Log group is being deleted.

  No messages will be accepted.
- `ERROR`: Log group is in failed state. ||
|| retentionPeriod | **[google.protobuf.Duration](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/duration)**

Log group entry retention period.

Entries will be present in group during this period. ||
|| dataStream | **string**

Data stream name ||
|#