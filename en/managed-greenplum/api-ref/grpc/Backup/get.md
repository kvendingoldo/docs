---
editable: false
sourcePath: en/_api-ref-grpc/mdb/greenplum/v1/api-ref/grpc/Backup/get.md
---

# Managed Service for Greenplum® API, gRPC: BackupService.Get {#Get}

Returns the specified backup of Greenplum® cluster.

## gRPC request

**rpc Get ([GetBackupRequest](#yandex.cloud.mdb.greenplum.v1.GetBackupRequest)) returns ([Backup](#yandex.cloud.mdb.greenplum.v1.Backup))**

## GetBackupRequest {#yandex.cloud.mdb.greenplum.v1.GetBackupRequest}

```json
{
  "backupId": "string"
}
```

#|
||Field | Description ||
|| backupId | **string**

Required field. ID of the backup to return. ||
|#

## Backup {#yandex.cloud.mdb.greenplum.v1.Backup}

```json
{
  "id": "string",
  "folderId": "string",
  "createdAt": "google.protobuf.Timestamp",
  "sourceClusterId": "string",
  "startedAt": "google.protobuf.Timestamp",
  "size": "int64",
  "type": "BackupCreationType",
  "method": "BackupMethod",
  "journalSize": "int64"
}
```

#|
||Field | Description ||
|| id | **string**

Required. ID of the backup. ||
|| folderId | **string**

ID of the folder that the backup belongs to. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Time when the backup operation was completed. ||
|| sourceClusterId | **string**

ID of the Greenplum® cluster that the backup was created for. ||
|| startedAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Time when the backup operation was started. ||
|| size | **int64**

Size of the backup in bytes. ||
|| type | enum **BackupCreationType**

How this backup was created (manual/automatic/etc...)

- `BACKUP_CREATION_TYPE_UNSPECIFIED`
- `AUTOMATED`: Backup created by automated daily schedule
- `MANUAL`: Backup created by user request ||
|| method | enum **BackupMethod**

Method of backup creation

- `BACKUP_METHOD_UNSPECIFIED`
- `BASE`: Base backup
- `INCREMENTAL`: Delta (incremental) Greenplum backup ||
|| journalSize | **int64**

Size of the journal associated with backup, in bytes ||
|#