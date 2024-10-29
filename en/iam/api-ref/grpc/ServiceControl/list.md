---
editable: false
sourcePath: en/_api-ref-grpc/iam/v1/api-ref/grpc/ServiceControl/list.md
---

# Identity and Access Management API, gRPC: ServiceControlService.List {#List}

Retrieves the list of Service in the specified resource container.

## gRPC request

**rpc List ([ListServicesRequest](#yandex.cloud.iam.v1.ListServicesRequest)) returns ([ListServicesResponse](#yandex.cloud.iam.v1.ListServicesResponse))**

## ListServicesRequest {#yandex.cloud.iam.v1.ListServicesRequest}

```json
{
  "resource": {
    "id": "string",
    "type": "string"
  },
  "pageSize": "int64",
  "pageToken": "string"
}
```

#|
||Field | Description ||
|| resource | **[Resource](#yandex.cloud.iam.v1.Resource)**

Required field. Resource container to list a services.

It is supported only resource-manager.cloud resource container now. ||
|| pageSize | **int64**

The maximum number of results per page to return. If the number of available
results is larger than `pageSize`,
the service returns a [ListServicesResponse.nextPageToken](#yandex.cloud.iam.v1.ListServicesResponse)
that can be used to get the next page of results in subsequent list requests.
Default value: 100 ||
|| pageToken | **string**

Page token. To get the next page of results, set `pageToken`
to the [ListServicesResponse.nextPageToken](#yandex.cloud.iam.v1.ListServicesResponse)
returned by a previous list request. ||
|#

## Resource {#yandex.cloud.iam.v1.Resource}

A Resource. For more information, see [Resource](/docs/iam/concepts/access-control/resources-with-access-control).

#|
||Field | Description ||
|| id | **string**

Required field. ID of the resource. ||
|| type | **string**

Required field. The type of the resource, e.g. resource-manager.folder, billing.account, compute.snapshot, etc. ||
|#

## ListServicesResponse {#yandex.cloud.iam.v1.ListServicesResponse}

```json
{
  "services": [
    {
      "serviceId": "string",
      "resource": {
        "id": "string",
        "type": "string"
      },
      "updatedAt": "google.protobuf.Timestamp",
      "status": "Status"
    }
  ],
  "nextPageToken": "string"
}
```

#|
||Field | Description ||
|| services[] | **[Service](#yandex.cloud.iam.v1.Service)**

List of Services. ||
|| nextPageToken | **string**

This token allows you to get the next page of results for list requests. If the number of results
is larger than [ListServicesRequest.pageSize](#yandex.cloud.iam.v1.ListServicesRequest), use
the `nextPageToken` as the value
for the [ListServicesRequest.pageToken](#yandex.cloud.iam.v1.ListServicesRequest) query parameter
in the next list request. Each subsequent list request will have its own
`nextPageToken` to continue paging through the results. ||
|#

## Service {#yandex.cloud.iam.v1.Service}

A Service.

#|
||Field | Description ||
|| serviceId | **string**

ID of the service. ||
|| resource | **[Resource](#yandex.cloud.iam.v1.Resource2)**

Resource that the service belongs to. ||
|| updatedAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Time of the last status update of the service. ||
|| status | enum **Status**

Current status of the service.

- `STATUS_UNSPECIFIED`
- `ENABLED`: The service is enabled.
- `PAUSED`: The service is paused.
- `DISABLED`: The service is disabled.
- `ENABLING`: The service is being enabled.
- `RESUMING`: The service is being resumed.
- `PAUSING`: The service is being paused.
- `DISABLING`: The service is being disabled.
- `ERROR`: The service is in error state.
- `DEFAULT`: The service could be auto enabled. ||
|#

## Resource {#yandex.cloud.iam.v1.Resource2}

A Resource. For more information, see [Resource](/docs/iam/concepts/access-control/resources-with-access-control).

#|
||Field | Description ||
|| id | **string**

Required field. ID of the resource. ||
|| type | **string**

Required field. The type of the resource, e.g. resource-manager.folder, billing.account, compute.snapshot, etc. ||
|#