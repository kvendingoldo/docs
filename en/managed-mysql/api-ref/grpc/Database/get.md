---
editable: false
sourcePath: en/_api-ref-grpc/mdb/mysql/v1/api-ref/grpc/Database/get.md
---

# Managed Service for MySQL API, gRPC: DatabaseService.Get {#Get}

Retrieves information about the specified database.

## gRPC request

**rpc Get ([GetDatabaseRequest](#yandex.cloud.mdb.mysql.v1.GetDatabaseRequest)) returns ([Database](#yandex.cloud.mdb.mysql.v1.Database))**

## GetDatabaseRequest {#yandex.cloud.mdb.mysql.v1.GetDatabaseRequest}

```json
{
  "clusterId": "string",
  "databaseName": "string"
}
```

#|
||Field | Description ||
|| clusterId | **string**

Required field. ID of the cluster that the database belongs to.

To get this ID, make a [ClusterService.List](/docs/managed-mysql/api-ref/grpc/Cluster/list#List) request. ||
|| databaseName | **string**

Required field. Name of the database to return information about.

To get this name, make a [DatabaseService.List](/docs/managed-mysql/api-ref/grpc/Database/list#List) request. ||
|#

## Database {#yandex.cloud.mdb.mysql.v1.Database}

```json
{
  "name": "string",
  "clusterId": "string"
}
```

An object that represents MySQL database.

See [the documentation](/docs/managed-mysql/operations/databases) for details.

#|
||Field | Description ||
|| name | **string**

Name of the database. ||
|| clusterId | **string**

ID of the cluster that the database belongs to. ||
|#