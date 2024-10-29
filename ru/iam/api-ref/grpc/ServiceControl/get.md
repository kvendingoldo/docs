---
editable: false
sourcePath: en/_api-ref-grpc/iam/v1/api-ref/grpc/ServiceControl/get.md
---

# Identity and Access Management API, gRPC: ServiceControlService.Get {#Get}

Returns the Service information in the specified resource container.

To get the list of available Services, make a [List](/docs/iam/api-ref/grpc/ServiceControl/list#List) request.

## gRPC request

**rpc Get ([GetServiceRequest](#yandex.cloud.iam.v1.GetServiceRequest)) returns ([Service](#yandex.cloud.iam.v1.Service))**

## GetServiceRequest {#yandex.cloud.iam.v1.GetServiceRequest}

```json
{
  "serviceId": "string",
  "resource": {
    "id": "string",
    "type": "string"
  }
}
```

#|
||Field | Description ||
|| serviceId | **string**

Required field. ID of the Service. ||
|| resource | **[Resource](#yandex.cloud.iam.v1.Resource)**

Required field. Resource container to get a service information in.

It is supported only resource-manager.cloud resource container now. ||
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

## Service {#yandex.cloud.iam.v1.Service}

```json
{
  "serviceId": "string",
  "resource": {
    "id": "string",
    "type": "string"
  },
  "updatedAt": "google.protobuf.Timestamp",
  "status": "Status"
}
```

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