---
editable: false
sourcePath: en/_api-ref-grpc/mdb/mongodb/v1/api-ref/grpc/Backup/get.md
---

# Managed Service for MongoDB API, gRPC: BackupService.Get {#Get}

Returns the specified MongoDB backup.

To get the list of available MongoDB backups, make a [List](/docs/managed-mongodb/api-ref/grpc/Backup/list#List) request.

## gRPC request

**rpc Get ([GetBackupRequest](#yandex.cloud.mdb.mongodb.v1.GetBackupRequest)) returns ([Backup](#yandex.cloud.mdb.mongodb.v1.Backup))**

## GetBackupRequest {#yandex.cloud.mdb.mongodb.v1.GetBackupRequest}

```json
{
  "backupId": "string"
}
```

#|
||Field | Description ||
|| backupId | **string**

Required field. ID of the backup to return information about.
To get the backup ID, use a [ClusterService.ListBackups](/docs/managed-mongodb/api-ref/grpc/Cluster/listBackups#ListBackups) request. ||
|#

## Backup {#yandex.cloud.mdb.mongodb.v1.Backup}

```json
{
  "id": "string",
  "folderId": "string",
  "createdAt": "google.protobuf.Timestamp",
  "sourceClusterId": "string",
  "startedAt": "google.protobuf.Timestamp",
  "sourceShardNames": [
    "string"
  ],
  "size": "int64",
  "type": "BackupType",
  "journalSize": "int64"
}
```

A MongoDB Backup resource. For more information, see the
[Developer's Guide](/docs/managed-mongodb/concepts).

#|
||Field | Description ||
|| id | **string**

ID of the backup. Required. ||
|| folderId | **string**

ID of the folder that the backup belongs to. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) text format
(i.e. when the backup operation was completed). ||
|| sourceClusterId | **string**

ID of the MongoDB cluster that the backup was created for. ||
|| startedAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Time when the backup operation was started. ||
|| sourceShardNames[] | **string**

Shard names used as a source for backup. ||
|| size | **int64**

Size of backup in bytes ||
|| type | enum **BackupType**

How this backup was created (manual/automatic/etc...)

- `BACKUP_TYPE_UNSPECIFIED`
- `AUTOMATED`: Backup created by automated daily schedule
- `MANUAL`: Backup created by user request ||
|| journalSize | **int64**

Size of the journal associated with backup, in bytes ||
|#