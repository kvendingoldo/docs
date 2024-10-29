---
editable: false
sourcePath: en/_api-ref-grpc/airflow/v1/api-ref/grpc/Cluster/update.md
---

# Managed Service for Apache Airflow™ API, gRPC: ClusterService.Update {#Update}

Updates the specified Apache Airflow cluster.

## gRPC request

**rpc Update ([UpdateClusterRequest](#yandex.cloud.airflow.v1.UpdateClusterRequest)) returns ([operation.Operation](#yandex.cloud.operation.Operation))**

## UpdateClusterRequest {#yandex.cloud.airflow.v1.UpdateClusterRequest}

```json
{
  "clusterId": "string",
  "updateMask": "google.protobuf.FieldMask",
  "name": "string",
  "description": "string",
  "labels": "string",
  "configSpec": {
    "airflow": {
      "config": "string"
    },
    "webserver": {
      "count": "int64",
      "resources": {
        "resourcePresetId": "string"
      }
    },
    "scheduler": {
      "count": "int64",
      "resources": {
        "resourcePresetId": "string"
      }
    },
    "triggerer": {
      "count": "int64",
      "resources": {
        "resourcePresetId": "string"
      }
    },
    "worker": {
      "minCount": "int64",
      "maxCount": "int64",
      "resources": {
        "resourcePresetId": "string"
      }
    },
    "dependencies": {
      "pipPackages": [
        "string"
      ],
      "debPackages": [
        "string"
      ]
    },
    "lockbox": {
      "enabled": "bool"
    }
  },
  "codeSync": {
    // Includes only one of the fields `s3`
    "s3": {
      "bucket": "string"
    }
    // end of the list of possible fields
  },
  "networkSpec": {
    "securityGroupIds": [
      "string"
    ]
  },
  "deletionProtection": "bool",
  "serviceAccountId": "string",
  "logging": {
    "enabled": "bool",
    // Includes only one of the fields `folderId`, `logGroupId`
    "folderId": "string",
    "logGroupId": "string",
    // end of the list of possible fields
    "minLevel": "Level"
  }
}
```

#|
||Field | Description ||
|| clusterId | **string**

Required field. ID of the Apache Airflow Cluster resource to update. ||
|| updateMask | **[google.protobuf.FieldMask](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/field-mask)**

Field mask that specifies which fields of the Apache Airflow Cluster resource should be updated. ||
|| name | **string**

New name of the cluster. ||
|| description | **string**

New description of the Apache Airflow cluster. ||
|| labels | **string**

Custom labels for the Apache Airflow cluster as `` key:value `` pairs. For example, "env": "prod".

The new set of labels will completely replace the old ones. To add a label, request the current
set with the [ClusterService.Get](/docs/managed-airflow/api-ref/grpc/Cluster/get#Get) method, then send an [ClusterService.Update](#Update) request with the new label added to the set. ||
|| configSpec | **[UpdateClusterConfigSpec](#yandex.cloud.airflow.v1.UpdateClusterConfigSpec)**

Configuration of Apache Airflow components. ||
|| codeSync | **[CodeSyncConfig](#yandex.cloud.airflow.v1.CodeSyncConfig)**

Parameters of the location and access to the code that will be executed in the cluster. ||
|| networkSpec | **[UpdateNetworkConfigSpec](#yandex.cloud.airflow.v1.UpdateNetworkConfigSpec)**

Network related configuration options. ||
|| deletionProtection | **bool**

Deletion Protection inhibits deletion of the cluster ||
|| serviceAccountId | **string**

Service account used to access Cloud resources.
For more information, see [documentation](/docs/managed-airflow/concepts/impersonation). ||
|| logging | **[LoggingConfig](#yandex.cloud.airflow.v1.LoggingConfig)**

Cloud Logging configuration. ||
|#

## UpdateClusterConfigSpec {#yandex.cloud.airflow.v1.UpdateClusterConfigSpec}

#|
||Field | Description ||
|| airflow | **[AirflowConfig](#yandex.cloud.airflow.v1.AirflowConfig)**

Configuration of the Apache Airflow application itself. ||
|| webserver | **[WebserverConfig](#yandex.cloud.airflow.v1.WebserverConfig)**

Configuration of webserver instances. ||
|| scheduler | **[SchedulerConfig](#yandex.cloud.airflow.v1.SchedulerConfig)**

Configuration of scheduler instances. ||
|| triggerer | **[TriggererConfig](#yandex.cloud.airflow.v1.TriggererConfig)**

Configuration of triggerer instances. ||
|| worker | **[WorkerConfig](#yandex.cloud.airflow.v1.WorkerConfig)**

Configuration of worker instances. ||
|| dependencies | **[Dependencies](#yandex.cloud.airflow.v1.Dependencies)**

The list of additional packages installed in the cluster. ||
|| lockbox | **[LockboxConfig](#yandex.cloud.airflow.v1.LockboxConfig)**

Configuration of Lockbox Secret Backend. ||
|#

## AirflowConfig {#yandex.cloud.airflow.v1.AirflowConfig}

#|
||Field | Description ||
|| config | **string**

Properties to be passed to Apache Airflow configuration file. ||
|#

## WebserverConfig {#yandex.cloud.airflow.v1.WebserverConfig}

#|
||Field | Description ||
|| count | **int64**

The number of webserver instances in the cluster. ||
|| resources | **[Resources](#yandex.cloud.airflow.v1.Resources)**

Resources allocated to webserver instances. ||
|#

## Resources {#yandex.cloud.airflow.v1.Resources}

#|
||Field | Description ||
|| resourcePresetId | **string**

ID of the preset for computational resources available to an instance (CPU, memory etc.). ||
|#

## SchedulerConfig {#yandex.cloud.airflow.v1.SchedulerConfig}

#|
||Field | Description ||
|| count | **int64**

The number of scheduler instances in the cluster. ||
|| resources | **[Resources](#yandex.cloud.airflow.v1.Resources)**

Resources allocated to scheduler instances. ||
|#

## TriggererConfig {#yandex.cloud.airflow.v1.TriggererConfig}

#|
||Field | Description ||
|| count | **int64**

The number of triggerer instances in the cluster. ||
|| resources | **[Resources](#yandex.cloud.airflow.v1.Resources)**

Resources allocated to triggerer instances. ||
|#

## WorkerConfig {#yandex.cloud.airflow.v1.WorkerConfig}

#|
||Field | Description ||
|| minCount | **int64**

The minimum number of worker instances in the cluster. ||
|| maxCount | **int64**

The maximum number of worker instances in the cluster. ||
|| resources | **[Resources](#yandex.cloud.airflow.v1.Resources)**

Resources allocated to worker instances. ||
|#

## Dependencies {#yandex.cloud.airflow.v1.Dependencies}

#|
||Field | Description ||
|| pipPackages[] | **string**

Python packages that are installed in the cluster. ||
|| debPackages[] | **string**

System packages that are installed in the cluster. ||
|#

## LockboxConfig {#yandex.cloud.airflow.v1.LockboxConfig}

#|
||Field | Description ||
|| enabled | **bool**

The setting allows to enable Lockbox Secret Backend. ||
|#

## CodeSyncConfig {#yandex.cloud.airflow.v1.CodeSyncConfig}

#|
||Field | Description ||
|| s3 | **[S3Config](#yandex.cloud.airflow.v1.S3Config)**

Includes only one of the fields `s3`. ||
|#

## S3Config {#yandex.cloud.airflow.v1.S3Config}

#|
||Field | Description ||
|| bucket | **string**

The name of the Object Storage bucket that stores DAG files used in the cluster. ||
|#

## UpdateNetworkConfigSpec {#yandex.cloud.airflow.v1.UpdateNetworkConfigSpec}

#|
||Field | Description ||
|| securityGroupIds[] | **string**

User security groups. ||
|#

## LoggingConfig {#yandex.cloud.airflow.v1.LoggingConfig}

#|
||Field | Description ||
|| enabled | **bool**

Logs generated by the Airflow components are delivered to Cloud Logging. ||
|| folderId | **string**

Logs should be written to default log group for specified folder.

Includes only one of the fields `folderId`, `logGroupId`.

Destination of log records. ||
|| logGroupId | **string**

Logs should be written to log group resolved by ID.

Includes only one of the fields `folderId`, `logGroupId`.

Destination of log records. ||
|| minLevel | enum **Level**

Minimum log entry level.

See [LogLevel.Level](/docs/logging/api-ref/grpc/Export/run#yandex.cloud.logging.v1.LogLevel.Level) for details.

- `LEVEL_UNSPECIFIED`: Default log level.

  Equivalent to not specifying log level at all.
- `TRACE`: Trace log level.

  Possible use case: verbose logging of some business logic.
- `DEBUG`: Debug log level.

  Possible use case: debugging special cases in application logic.
- `INFO`: Info log level.

  Mostly used for information messages.
- `WARN`: Warn log level.

  May be used to alert about significant events.
- `ERROR`: Error log level.

  May be used to alert about errors in infrastructure, logic, etc.
- `FATAL`: Fatal log level.

  May be used to alert about unrecoverable failures and events. ||
|#

## operation.Operation {#yandex.cloud.operation.Operation}

```json
{
  "id": "string",
  "description": "string",
  "createdAt": "google.protobuf.Timestamp",
  "createdBy": "string",
  "modifiedAt": "google.protobuf.Timestamp",
  "done": "bool",
  "metadata": {
    "clusterId": "string"
  },
  // Includes only one of the fields `error`, `response`
  "error": "google.rpc.Status",
  "response": {
    "id": "string",
    "folderId": "string",
    "createdAt": "google.protobuf.Timestamp",
    "name": "string",
    "description": "string",
    "labels": "string",
    "monitoring": [
      {
        "name": "string",
        "description": "string",
        "link": "string"
      }
    ],
    "config": {
      "versionId": "string",
      "airflow": {
        "config": "string"
      },
      "webserver": {
        "count": "int64",
        "resources": {
          "resourcePresetId": "string"
        }
      },
      "scheduler": {
        "count": "int64",
        "resources": {
          "resourcePresetId": "string"
        }
      },
      "triggerer": {
        "count": "int64",
        "resources": {
          "resourcePresetId": "string"
        }
      },
      "worker": {
        "minCount": "int64",
        "maxCount": "int64",
        "resources": {
          "resourcePresetId": "string"
        }
      },
      "dependencies": {
        "pipPackages": [
          "string"
        ],
        "debPackages": [
          "string"
        ]
      },
      "lockbox": {
        "enabled": "bool"
      }
    },
    "health": "Health",
    "status": "Status",
    "network": {
      "subnetIds": [
        "string"
      ],
      "securityGroupIds": [
        "string"
      ]
    },
    "codeSync": {
      // Includes only one of the fields `s3`
      "s3": {
        "bucket": "string"
      }
      // end of the list of possible fields
    },
    "deletionProtection": "bool",
    "webserverUrl": "string",
    "serviceAccountId": "string",
    "logging": {
      "enabled": "bool",
      // Includes only one of the fields `folderId`, `logGroupId`
      "folderId": "string",
      "logGroupId": "string",
      // end of the list of possible fields
      "minLevel": "Level"
    }
  }
  // end of the list of possible fields
}
```

An Operation resource. For more information, see [Operation](/docs/api-design-guide/concepts/operation).

#|
||Field | Description ||
|| id | **string**

ID of the operation. ||
|| description | **string**

Description of the operation. 0-256 characters long. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp. ||
|| createdBy | **string**

ID of the user or service account who initiated the operation. ||
|| modifiedAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

The time when the Operation resource was last modified. ||
|| done | **bool**

If the value is `false`, it means the operation is still in progress.
If `true`, the operation is completed, and either `error` or `response` is available. ||
|| metadata | **[UpdateClusterMetadata](#yandex.cloud.airflow.v1.UpdateClusterMetadata)**

Service-specific metadata associated with the operation.
It typically contains the ID of the target resource that the operation is performed on.
Any method that returns a long-running operation should document the metadata type, if any. ||
|| error | **[google.rpc.Status](https://cloud.google.com/tasks/docs/reference/rpc/google.rpc#status)**

The error result of the operation in case of failure or cancellation.

Includes only one of the fields `error`, `response`.

The operation result.
If `done == false` and there was no failure detected, neither `error` nor `response` is set.
If `done == false` and there was a failure detected, `error` is set.
If `done == true`, exactly one of `error` or `response` is set. ||
|| response | **[Cluster](#yandex.cloud.airflow.v1.Cluster)**

The normal response of the operation in case of success.
If the original method returns no data on success, such as Delete,
the response is [google.protobuf.Empty](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#google.protobuf.Empty).
If the original method is the standard Create/Update,
the response should be the target resource of the operation.
Any method that returns a long-running operation should document the response type, if any.

Includes only one of the fields `error`, `response`.

The operation result.
If `done == false` and there was no failure detected, neither `error` nor `response` is set.
If `done == false` and there was a failure detected, `error` is set.
If `done == true`, exactly one of `error` or `response` is set. ||
|#

## UpdateClusterMetadata {#yandex.cloud.airflow.v1.UpdateClusterMetadata}

#|
||Field | Description ||
|| clusterId | **string**

ID of the Apache Airflow Cluster resource that is being updated. ||
|#

## Cluster {#yandex.cloud.airflow.v1.Cluster}

Apache Airflow cluster.

#|
||Field | Description ||
|| id | **string**

Unique ID of the Apache Airflow cluster.
This ID is assigned by Cloud during cluster creation. ||
|| folderId | **string**

ID of the folder that the Apache Airflow cluster belongs to. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

The time when the Apache Airflow cluster was created. ||
|| name | **string**

Name of the Apache Airflow cluster.
The name is unique within the folder. 1-64 characters long. ||
|| description | **string**

Description of the Apache Airflow cluster. 0-256 characters long. ||
|| labels | **string**

Resource labels as `key:value` pairs. Maximum of 64 per resource. ||
|| monitoring[] | **[Monitoring](#yandex.cloud.airflow.v1.Monitoring)**

Monitoring systems relevant to the Apache Airflow cluster. ||
|| config | **[ClusterConfig](#yandex.cloud.airflow.v1.ClusterConfig)**

Configuration of Apache Airflow components. ||
|| health | enum **Health**

Aggregated cluster health.

- `HEALTH_UNKNOWN`: Cluster is in unknown state (we have no data).
- `ALIVE`: Cluster is alive and well.
- `DEAD`: Cluster is inoperable (it cannot perform any of its essential functions).
- `DEGRADED`: Cluster is partially alive (it can perform some of its essential functions). ||
|| status | enum **Status**

Cluster status.

- `STATUS_UNKNOWN`: Cluster state is unknown.
- `CREATING`: Cluster is being created.
- `RUNNING`: Cluster is running normally.
- `ERROR`: Cluster encountered a problem and cannot operate.
- `STOPPING`: Cluster is stopping.
- `STOPPED`: Cluster is stopped.
- `STARTING`: Cluster is starting.
- `UPDATING`: Cluster is being updated. ||
|| network | **[NetworkConfig](#yandex.cloud.airflow.v1.NetworkConfig)**

Network related configuration options. ||
|| codeSync | **[CodeSyncConfig](#yandex.cloud.airflow.v1.CodeSyncConfig2)**

Parameters of the location and access to the code that will be executed in the cluster. ||
|| deletionProtection | **bool**

Deletion Protection inhibits deletion of the cluster. ||
|| webserverUrl | **string**

Address of Apache Airflow web UI. ||
|| serviceAccountId | **string**

Service account used to access Cloud resources.
For more information, see [documentation](/docs/managed-airflow/concepts/impersonation). ||
|| logging | **[LoggingConfig](#yandex.cloud.airflow.v1.LoggingConfig2)**

Cloud Logging configuration. ||
|#

## Monitoring {#yandex.cloud.airflow.v1.Monitoring}

Monitoring system.

#|
||Field | Description ||
|| name | **string**

Name of the monitoring system. ||
|| description | **string**

Description of the monitoring system. ||
|| link | **string**

Link to the monitoring system. ||
|#

## ClusterConfig {#yandex.cloud.airflow.v1.ClusterConfig}

#|
||Field | Description ||
|| versionId | **string**

Version of Apache that runs on the cluster. ||
|| airflow | **[AirflowConfig](#yandex.cloud.airflow.v1.AirflowConfig2)**

Configuration of the Apache Airflow application itself. ||
|| webserver | **[WebserverConfig](#yandex.cloud.airflow.v1.WebserverConfig2)**

Required field. Configuration of webserver instances. ||
|| scheduler | **[SchedulerConfig](#yandex.cloud.airflow.v1.SchedulerConfig2)**

Required field. Configuration of scheduler instances. ||
|| triggerer | **[TriggererConfig](#yandex.cloud.airflow.v1.TriggererConfig2)**

Configuration of triggerer instances. ||
|| worker | **[WorkerConfig](#yandex.cloud.airflow.v1.WorkerConfig2)**

Required field. Configuration of worker instances. ||
|| dependencies | **[Dependencies](#yandex.cloud.airflow.v1.Dependencies2)**

The list of additional packages installed in the cluster. ||
|| lockbox | **[LockboxConfig](#yandex.cloud.airflow.v1.LockboxConfig2)**

Configuration of Lockbox Secret Backend. ||
|#

## AirflowConfig {#yandex.cloud.airflow.v1.AirflowConfig2}

#|
||Field | Description ||
|| config | **string**

Properties to be passed to Apache Airflow configuration file. ||
|#

## WebserverConfig {#yandex.cloud.airflow.v1.WebserverConfig2}

#|
||Field | Description ||
|| count | **int64**

The number of webserver instances in the cluster. ||
|| resources | **[Resources](#yandex.cloud.airflow.v1.Resources2)**

Resources allocated to webserver instances. ||
|#

## Resources {#yandex.cloud.airflow.v1.Resources2}

#|
||Field | Description ||
|| resourcePresetId | **string**

ID of the preset for computational resources available to an instance (CPU, memory etc.). ||
|#

## SchedulerConfig {#yandex.cloud.airflow.v1.SchedulerConfig2}

#|
||Field | Description ||
|| count | **int64**

The number of scheduler instances in the cluster. ||
|| resources | **[Resources](#yandex.cloud.airflow.v1.Resources2)**

Resources allocated to scheduler instances. ||
|#

## TriggererConfig {#yandex.cloud.airflow.v1.TriggererConfig2}

#|
||Field | Description ||
|| count | **int64**

The number of triggerer instances in the cluster. ||
|| resources | **[Resources](#yandex.cloud.airflow.v1.Resources2)**

Resources allocated to triggerer instances. ||
|#

## WorkerConfig {#yandex.cloud.airflow.v1.WorkerConfig2}

#|
||Field | Description ||
|| minCount | **int64**

The minimum number of worker instances in the cluster. ||
|| maxCount | **int64**

The maximum number of worker instances in the cluster. ||
|| resources | **[Resources](#yandex.cloud.airflow.v1.Resources2)**

Resources allocated to worker instances. ||
|#

## Dependencies {#yandex.cloud.airflow.v1.Dependencies2}

#|
||Field | Description ||
|| pipPackages[] | **string**

Python packages that are installed in the cluster. ||
|| debPackages[] | **string**

System packages that are installed in the cluster. ||
|#

## LockboxConfig {#yandex.cloud.airflow.v1.LockboxConfig2}

#|
||Field | Description ||
|| enabled | **bool**

The setting allows to enable Lockbox Secret Backend. ||
|#

## NetworkConfig {#yandex.cloud.airflow.v1.NetworkConfig}

#|
||Field | Description ||
|| subnetIds[] | **string**

IDs of VPC network subnets where instances of the cluster are attached. ||
|| securityGroupIds[] | **string**

User security groups. ||
|#

## CodeSyncConfig {#yandex.cloud.airflow.v1.CodeSyncConfig2}

#|
||Field | Description ||
|| s3 | **[S3Config](#yandex.cloud.airflow.v1.S3Config2)**

Includes only one of the fields `s3`. ||
|#

## S3Config {#yandex.cloud.airflow.v1.S3Config2}

#|
||Field | Description ||
|| bucket | **string**

The name of the Object Storage bucket that stores DAG files used in the cluster. ||
|#

## LoggingConfig {#yandex.cloud.airflow.v1.LoggingConfig2}

#|
||Field | Description ||
|| enabled | **bool**

Logs generated by the Airflow components are delivered to Cloud Logging. ||
|| folderId | **string**

Logs should be written to default log group for specified folder.

Includes only one of the fields `folderId`, `logGroupId`.

Destination of log records. ||
|| logGroupId | **string**

Logs should be written to log group resolved by ID.

Includes only one of the fields `folderId`, `logGroupId`.

Destination of log records. ||
|| minLevel | enum **Level**

Minimum log entry level.

See [LogLevel.Level](/docs/logging/api-ref/grpc/Export/run#yandex.cloud.logging.v1.LogLevel.Level) for details.

- `LEVEL_UNSPECIFIED`: Default log level.

  Equivalent to not specifying log level at all.
- `TRACE`: Trace log level.

  Possible use case: verbose logging of some business logic.
- `DEBUG`: Debug log level.

  Possible use case: debugging special cases in application logic.
- `INFO`: Info log level.

  Mostly used for information messages.
- `WARN`: Warn log level.

  May be used to alert about significant events.
- `ERROR`: Error log level.

  May be used to alert about errors in infrastructure, logic, etc.
- `FATAL`: Fatal log level.

  May be used to alert about unrecoverable failures and events. ||
|#