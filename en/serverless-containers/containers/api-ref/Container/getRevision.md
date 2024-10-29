---
editable: false
sourcePath: en/_api-ref/serverless/containers/v1/containers/api-ref/Container/getRevision.md
---

# Serverless Containers Service, REST: Container.GetRevision {#GetRevision}

Returns the specified revision of a container.

To get the list of available revision, make a [ListRevisions](/docs/serverless/containers/api-ref/Container/listRevisions#ListRevisions) request.

## HTTP request

```
GET https://serverless-containers.{{ api-host }}/containers/v1/revisions/{containerRevisionId}
```

## Path parameters

#|
||Field | Description ||
|| containerRevisionId | **string**

Required field. ID of the revision to return.

To get a revision ID make a [ContainerService.ListRevisions](/docs/serverless/containers/api-ref/Container/listRevisions#ListRevisions) request. ||
|#

## Response {#yandex.cloud.serverless.containers.v1.Revision}

**HTTP Code: 200 - OK**

```json
{
  "id": "string",
  "containerId": "string",
  "description": "string",
  "createdAt": "string",
  "image": {
    "imageUrl": "string",
    "imageDigest": "string",
    "command": {
      "command": [
        "string"
      ]
    },
    "args": {
      "args": [
        "string"
      ]
    },
    "environment": "string",
    "workingDir": "string"
  },
  "resources": {
    "memory": "string",
    "cores": "string",
    "coreFraction": "string"
  },
  "executionTimeout": "string",
  "concurrency": "string",
  "serviceAccountId": "string",
  "status": "string",
  "secrets": [
    {
      "id": "string",
      "versionId": "string",
      "key": "string",
      // Includes only one of the fields `environmentVariable`
      "environmentVariable": "string"
      // end of the list of possible fields
    }
  ],
  "connectivity": {
    "networkId": "string",
    "subnetIds": [
      "string"
    ]
  },
  "provisionPolicy": {
    "minInstances": "string"
  },
  "scalingPolicy": {
    "zoneInstancesLimit": "string",
    "zoneRequestsLimit": "string"
  },
  "logOptions": {
    "disabled": "boolean",
    // Includes only one of the fields `logGroupId`, `folderId`
    "logGroupId": "string",
    "folderId": "string",
    // end of the list of possible fields
    "minLevel": "string"
  },
  "storageMounts": [
    {
      "bucketId": "string",
      "prefix": "string",
      "readOnly": "boolean",
      "mountPointPath": "string"
    }
  ],
  "mounts": [
    {
      "mountPointPath": "string",
      "mode": "string",
      // Includes only one of the fields `objectStorage`, `ephemeralDiskSpec`
      "objectStorage": {
        "bucketId": "string",
        "prefix": "string"
      },
      "ephemeralDiskSpec": {
        "size": "string",
        "blockSize": "string"
      }
      // end of the list of possible fields
    }
  ]
}
```

#|
||Field | Description ||
|| id | **string**

ID of the revision. ||
|| containerId | **string**

ID of the container that the revision belongs to. ||
|| description | **string**

Description of the revision. ||
|| createdAt | **string** (date-time)

Creation timestamp for the revision.

String in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) text format. The range of possible values is from
`0001-01-01T00:00:00Z` to `9999-12-31T23:59:59.999999999Z`, i.e. from 0 to 9 digits for fractions of a second.

To work with values in this field, use the APIs described in the
[Protocol Buffers reference](https://developers.google.com/protocol-buffers/docs/reference/overview).
In some languages, built-in datetime utilities do not support nanosecond precision (9 digits). ||
|| image | **[Image](#yandex.cloud.serverless.containers.v1.Image)**

Image configuration for the revision. ||
|| resources | **[Resources](#yandex.cloud.serverless.containers.v1.Resources)**

Resources allocated to the revision. ||
|| executionTimeout | **string** (duration)

Timeout for the execution of the revision.

If the timeout is exceeded, Serverless Containers responds with a 504 HTTP code. ||
|| concurrency | **string** (int64)

The number of concurrent requests allowed per container instance. ||
|| serviceAccountId | **string**

ID of the service account associated with the revision. ||
|| status | **enum** (Status)

Status of the revision.

- `STATUS_UNSPECIFIED`
- `CREATING`: Revision is being created.
- `ACTIVE`: Revision is currently used by the container.
- `OBSOLETE`: Revision is not used by the container. May be deleted later. ||
|| secrets[] | **[Secret](#yandex.cloud.serverless.containers.v1.Secret)**

Yandex Lockbox secrets to be used by the revision. ||
|| connectivity | **[Connectivity](#yandex.cloud.serverless.containers.v1.Connectivity)**

Network access. If specified the revision will be attached to specified network/subnet(s). ||
|| provisionPolicy | **[ProvisionPolicy](#yandex.cloud.serverless.containers.v1.ProvisionPolicy)**

Policy for provisioning instances of the revision.

The policy is only applied when the revision is ACTIVE. ||
|| scalingPolicy | **[ScalingPolicy](#yandex.cloud.serverless.containers.v1.ScalingPolicy)**

Policy for scaling instances of the revision. ||
|| logOptions | **[LogOptions](#yandex.cloud.serverless.containers.v1.LogOptions)**

Options for logging from the container. ||
|| storageMounts[] | **[StorageMount](#yandex.cloud.serverless.containers.v1.StorageMount)**

S3 mounts to be used by the revision. ||
|| mounts[] | **[Mount](#yandex.cloud.serverless.containers.v1.Mount)**

Mounts to be used by the revision. ||
|#

## Image {#yandex.cloud.serverless.containers.v1.Image}

Revision image specification.

#|
||Field | Description ||
|| imageUrl | **string**

Image URL, that is used by the revision. ||
|| imageDigest | **string**

Digest of the image. Calculated at creation time. ||
|| command | **[Command](#yandex.cloud.serverless.containers.v1.Command)**

Override for the image's ENTRYPOINT. ||
|| args | **[Args](#yandex.cloud.serverless.containers.v1.Args)**

Override for the image's CMD. ||
|| environment | **string**

Additional environment for the container. ||
|| workingDir | **string**

Override for the image's WORKDIR. ||
|#

## Command {#yandex.cloud.serverless.containers.v1.Command}

#|
||Field | Description ||
|| command[] | **string**

Command that will override ENTRYPOINT of an image.

Commands will be executed as is. The runtime will not substitute environment
variables or execute shell commands. If one wants to do that, they should
invoke shell interpreter with an appropriate shell script. ||
|#

## Args {#yandex.cloud.serverless.containers.v1.Args}

#|
||Field | Description ||
|| args[] | **string**

Arguments that will override CMD of an image.

Arguments will be passed as is. The runtime will not substitute environment
variables or execute shell commands. If one wants to do that, they should
invoke shell interpreter with an appropriate shell script. ||
|#

## Resources {#yandex.cloud.serverless.containers.v1.Resources}

Resources allocated to a revision.

#|
||Field | Description ||
|| memory | **string** (int64)

Amount of memory available to the revision, specified in bytes, multiple of 128MB. ||
|| cores | **string** (int64)

Number of cores available to the revision. ||
|| coreFraction | **string** (int64)

Specifies baseline performance for a core in percent, multiple of 5%.
Should be 100% for cores > 1. ||
|#

## Secret {#yandex.cloud.serverless.containers.v1.Secret}

Secret that is available to the container at run time.

#|
||Field | Description ||
|| id | **string**

ID of Yandex Lockbox secret. ||
|| versionId | **string**

ID of Yandex Lockbox secret. ||
|| key | **string**

Key in secret's payload, which value to be delivered into container environment. ||
|| environmentVariable | **string**

Environment variable in which secret's value is delivered.

Includes only one of the fields `environmentVariable`. ||
|#

## Connectivity {#yandex.cloud.serverless.containers.v1.Connectivity}

Revision connectivity specification.

#|
||Field | Description ||
|| networkId | **string**

Network the revision will have access to. ||
|| subnetIds[] | **string**

The list of subnets (from the same network) the revision can be attached to.

Deprecated, it is sufficient to specify only network_id, without the list of subnet_ids. ||
|#

## ProvisionPolicy {#yandex.cloud.serverless.containers.v1.ProvisionPolicy}

#|
||Field | Description ||
|| minInstances | **string** (int64)

Minimum number of guaranteed provisioned container instances for all zones
in total. ||
|#

## ScalingPolicy {#yandex.cloud.serverless.containers.v1.ScalingPolicy}

#|
||Field | Description ||
|| zoneInstancesLimit | **string** (int64)

Upper limit for instance count in each zone.
0 means no limit. ||
|| zoneRequestsLimit | **string** (int64)

Upper limit of requests count in each zone.
0 means no limit. ||
|#

## LogOptions {#yandex.cloud.serverless.containers.v1.LogOptions}

#|
||Field | Description ||
|| disabled | **boolean**

Is logging from container disabled. ||
|| logGroupId | **string**

Entry should be written to log group resolved by ID.

Includes only one of the fields `logGroupId`, `folderId`.

Log entries destination. ||
|| folderId | **string**

Entry should be written to default log group for specified folder.

Includes only one of the fields `logGroupId`, `folderId`.

Log entries destination. ||
|| minLevel | **enum** (Level)

Minimum log entry level.

See [LogLevel.Level](/docs/logging/api-ref/Export/run#yandex.cloud.logging.v1.LogLevel.Level) for details.

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

## StorageMount {#yandex.cloud.serverless.containers.v1.StorageMount}

#|
||Field | Description ||
|| bucketId | **string**

Required field. S3 bucket name for mounting. ||
|| prefix | **string**

S3 bucket prefix for mounting. ||
|| readOnly | **boolean**

Is mount read only. ||
|| mountPointPath | **string**

Required field. Mount point path inside the container for mounting. ||
|#

## Mount {#yandex.cloud.serverless.containers.v1.Mount}

Mount contains an information about version's external storage mount

#|
||Field | Description ||
|| mountPointPath | **string**

Required field. The absolute mount point path inside the container for mounting. ||
|| mode | **enum** (Mode)

Mount's mode

- `MODE_UNSPECIFIED`
- `READ_ONLY`
- `READ_WRITE` ||
|| objectStorage | **[ObjectStorage](#yandex.cloud.serverless.containers.v1.Mount.ObjectStorage)**

Object storage mounts

Includes only one of the fields `objectStorage`, `ephemeralDiskSpec`.

Target mount option ||
|| ephemeralDiskSpec | **[DiskSpec](#yandex.cloud.serverless.containers.v1.Mount.DiskSpec)**

Working disk (worker-local non-shared read-write NBS disk templates)

Includes only one of the fields `objectStorage`, `ephemeralDiskSpec`.

Target mount option ||
|#

## ObjectStorage {#yandex.cloud.serverless.containers.v1.Mount.ObjectStorage}

ObjectStorage as a mount

#|
||Field | Description ||
|| bucketId | **string**

Required field. ObjectStorage bucket name for mounting. ||
|| prefix | **string**

ObjectStorage bucket prefix for mounting. ||
|#

## DiskSpec {#yandex.cloud.serverless.containers.v1.Mount.DiskSpec}

Disk as a mount

#|
||Field | Description ||
|| size | **string** (int64)

The size of disk for mount in bytes ||
|| blockSize | **string** (int64)

Optional block size of disk for mount in bytes ||
|#