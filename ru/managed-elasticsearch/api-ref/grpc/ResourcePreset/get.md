---
editable: false
sourcePath: en/_api-ref-grpc/mdb/elasticsearch/v1/api-ref/grpc/ResourcePreset/get.md
---

# Managed Service for Elasticsearch API, gRPC: ResourcePresetService.Get {#Get}

Returns the specified resource preset.

To get the list of available resource presets, make a [List](/docs/managed-elasticsearch/api-ref/grpc/ResourcePreset/list#List) request.

## gRPC request

**rpc Get ([GetResourcePresetRequest](#yandex.cloud.mdb.elasticsearch.v1.GetResourcePresetRequest)) returns ([ResourcePreset](#yandex.cloud.mdb.elasticsearch.v1.ResourcePreset))**

## GetResourcePresetRequest {#yandex.cloud.mdb.elasticsearch.v1.GetResourcePresetRequest}

```json
{
  "resourcePresetId": "string"
}
```

#|
||Field | Description ||
|| resourcePresetId | **string**

Required field. ID of the resource preset to return.

To get the resource preset ID, use a [ResourcePresetService.List](/docs/managed-elasticsearch/api-ref/grpc/ResourcePreset/list#List) request. ||
|#

## ResourcePreset {#yandex.cloud.mdb.elasticsearch.v1.ResourcePreset}

```json
{
  "id": "string",
  "zoneIds": [
    "string"
  ],
  "cores": "int64",
  "memory": "int64"
}
```

A ResourcePreset resource for describing hardware configuration presets.

#|
||Field | Description ||
|| id | **string**

ID of the resource preset. ||
|| zoneIds[] | **string**

IDs of availability zones where the resource preset is available. ||
|| cores | **int64**

Number of CPU cores for an Elasticsearch node created with the preset. ||
|| memory | **int64**

RAM volume for an Elasticsearch node created with the preset, in bytes. ||
|#