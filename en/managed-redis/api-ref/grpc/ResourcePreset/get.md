---
editable: false
sourcePath: en/_api-ref-grpc/mdb/redis/v1/api-ref/grpc/ResourcePreset/get.md
---

# Managed Service for Redis API, gRPC: ResourcePresetService.Get {#Get}

Returns the specified resource preset.

To get the list of available resource presets, make a [List](/docs/managed-redis/api-ref/grpc/ResourcePreset/list#List) request.

## gRPC request

**rpc Get ([GetResourcePresetRequest](#yandex.cloud.mdb.redis.v1.GetResourcePresetRequest)) returns ([ResourcePreset](#yandex.cloud.mdb.redis.v1.ResourcePreset))**

## GetResourcePresetRequest {#yandex.cloud.mdb.redis.v1.GetResourcePresetRequest}

```json
{
  "resourcePresetId": "string"
}
```

#|
||Field | Description ||
|| resourcePresetId | **string**

Required field. ID of the resource preset to return.
To get the resource preset ID, use a [ResourcePresetService.List](/docs/managed-redis/api-ref/grpc/ResourcePreset/list#List) request. ||
|#

## ResourcePreset {#yandex.cloud.mdb.redis.v1.ResourcePreset}

```json
{
  "id": "string",
  "zoneIds": [
    "string"
  ],
  "memory": "int64",
  "cores": "int64"
}
```

A resource preset that describes hardware configuration for a host.

#|
||Field | Description ||
|| id | **string**

ID of the resource preset. ||
|| zoneIds[] | **string**

IDs of availability zones where the resource preset is available. ||
|| memory | **int64**

RAM volume for a Redis host created with the preset, in bytes. ||
|| cores | **int64**

Number of CPU cores for a Redis host created with the preset. ||
|#