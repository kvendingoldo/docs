---
editable: false
sourcePath: en/_api-ref-grpc/organizationmanager/v1/api-ref/grpc/GroupMapping/get.md
---

# Cloud Organization API, gRPC: GroupMappingService.Get {#Get}

Returns a group mapping configured for the specific federation
If a federation does not exist this call will return an error
NOT_FOUND will be returned
If a federation exist, but has not ever been configured for group mapping
the call FAILED_PRECONDITION will be returned.

## gRPC request

**rpc Get ([GetGroupMappingRequest](#yandex.cloud.organizationmanager.v1.GetGroupMappingRequest)) returns ([GetGroupMappingResponse](#yandex.cloud.organizationmanager.v1.GetGroupMappingResponse))**

## GetGroupMappingRequest {#yandex.cloud.organizationmanager.v1.GetGroupMappingRequest}

```json
{
  "federationId": "string"
}
```

#|
||Field | Description ||
|| federationId | **string**

Required field.  ||
|#

## GetGroupMappingResponse {#yandex.cloud.organizationmanager.v1.GetGroupMappingResponse}

```json
{
  "groupMapping": {
    "federationId": "string",
    "enabled": "bool"
  }
}
```

#|
||Field | Description ||
|| groupMapping | **[GroupMapping](#yandex.cloud.organizationmanager.v1.GroupMapping)** ||
|#

## GroupMapping {#yandex.cloud.organizationmanager.v1.GroupMapping}

Group synchronization status for a specific federation
Absence of this object for a federation means that there is no group synchronization set of for the federation.

#|
||Field | Description ||
|| federationId | **string**

Federation id ||
|| enabled | **bool**

Flag to show whether group synchronization should be enabled for this federation. ||
|#