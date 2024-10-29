---
editable: false
sourcePath: en/_api-ref-grpc/mdb/mysql/v1/api-ref/grpc/Backup/get.md
---

# Managed Service for MySQL API, gRPC: BackupService.Get {#Get}

Retrieves information about the specified backup.

## gRPC request

**rpc Get ([GetBackupRequest](#yandex.cloud.mdb.mysql.v1.GetBackupRequest)) returns ([Backup](#yandex.cloud.mdb.mysql.v1.Backup))**

## GetBackupRequest {#yandex.cloud.mdb.mysql.v1.GetBackupRequest}

```json
{
  "backupId": "string"
}
```

#|
||Field | Description ||
|| backupId | **string**

Required field. ID of the backup to return information about.

To get this ID, make a [BackupService.List](/docs/managed-mysql/api-ref/grpc/Backup/list#List) request (lists all backups in a folder) or a [ClusterService.ListBackups](/docs/managed-mysql/api-ref/grpc/Cluster/listBackups#ListBackups) request (lists all backups for an existing cluster). ||
|#

## Backup {#yandex.cloud.mdb.mysql.v1.Backup}

```json
{
  "id": "string",
  "folderId": "string",
  "createdAt": "google.protobuf.Timestamp",
  "sourceClusterId": "string",
  "startedAt": "google.protobuf.Timestamp",
  "size": "int64",
  "type": "BackupCreationType",
  "status": "BackupStatus"
}
```

An object that represents MySQL backup.

See [the documentation](/docs/managed-mysql/concepts/backup) for details.

#|
||Field | Description ||
|| id | **string**

Required field. ID of the backup. ||
|| folderId | **string**

ID of the folder that the backup belongs to. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp (the time when the backup operation was completed). ||
|| sourceClusterId | **string**

ID of the cluster that the backup was created for. ||
|| startedAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Start timestamp (the time when the backup operation was started). ||
|| size | **int64**

Size of backup, in bytes ||
|| type | enum **BackupCreationType**

How this backup was created (manual/automatic/etc...)

- `BACKUP_CREATION_TYPE_UNSPECIFIED`
- `AUTOMATED`: Backup created by automated daily schedule
- `MANUAL`: Backup created by user request ||
|| status | enum **BackupStatus**

Status of backup

- `BACKUP_STATUS_UNSPECIFIED`
- `DONE`: Backup is done
- `CREATING`: Backup is creating ||
|#