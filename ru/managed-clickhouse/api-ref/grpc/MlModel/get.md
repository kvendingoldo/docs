---
editable: false
sourcePath: en/_api-ref-grpc/mdb/clickhouse/v1/api-ref/grpc/MlModel/get.md
---

# Managed Service for ClickHouse API, gRPC: MlModelService.Get {#Get}

Returns the specified machine learning model.

To get the list of all available models, make a [List](/docs/managed-clickhouse/api-ref/grpc/MlModel/list#List) request.

## gRPC request

**rpc Get ([GetMlModelRequest](#yandex.cloud.mdb.clickhouse.v1.GetMlModelRequest)) returns ([MlModel](#yandex.cloud.mdb.clickhouse.v1.MlModel))**

## GetMlModelRequest {#yandex.cloud.mdb.clickhouse.v1.GetMlModelRequest}

```json
{
  "clusterId": "string",
  "mlModelName": "string"
}
```

#|
||Field | Description ||
|| clusterId | **string**

Required field. ID of the cluster that the model belongs to. ||
|| mlModelName | **string**

Required field. Name of the model to return.

To get a model name make a [MlModelService.List](/docs/managed-clickhouse/api-ref/grpc/MlModel/list#List) request. ||
|#

## MlModel {#yandex.cloud.mdb.clickhouse.v1.MlModel}

```json
{
  "name": "string",
  "clusterId": "string",
  "type": "MlModelType",
  "uri": "string"
}
```

#|
||Field | Description ||
|| name | **string**

Name of the the model. ||
|| clusterId | **string**

ID of the ClickHouse cluster that the model belongs to. ||
|| type | enum **MlModelType**

Type of the model.

- `ML_MODEL_TYPE_UNSPECIFIED`
- `ML_MODEL_TYPE_CATBOOST`: CatBoost model. ||
|| uri | **string**

Model file URL. You can only use models stored in Object Storage. ||
|#