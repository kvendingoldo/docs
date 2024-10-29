---
editable: false
sourcePath: en/_api-ref/mdb/mysql/v1/api-ref/Cluster/addHosts.md
---

# Managed Service for MySQL API, REST: Cluster.AddHosts {#AddHosts}

Adds new hosts in a cluster.

## HTTP request

```
POST https://{{ api-host-mdb }}/managed-mysql/v1/clusters/{clusterId}/hosts:batchCreate
```

## Path parameters

#|
||Field | Description ||
|| clusterId | **string**

Required field. ID of the cluster to add hosts to.

To get this ID, make a [ClusterService.List](/docs/managed-mysql/api-ref/Cluster/list#List) request. ||
|#

## Body parameters {#yandex.cloud.mdb.mysql.v1.AddClusterHostsRequest}

```json
{
  "hostSpecs": [
    {
      "zoneId": "string",
      "subnetId": "string",
      "assignPublicIp": "boolean",
      "replicationSource": "string",
      "backupPriority": "string",
      "priority": "string"
    }
  ]
}
```

#|
||Field | Description ||
|| hostSpecs[] | **[HostSpec](#yandex.cloud.mdb.mysql.v1.HostSpec)**

Configuration of the newly added hosts. ||
|#

## HostSpec {#yandex.cloud.mdb.mysql.v1.HostSpec}

#|
||Field | Description ||
|| zoneId | **string**

ID of the availability zone where the host resides.

To get a list of available zones, make the [yandex.cloud.compute.v1.ZoneService.List](/docs/compute/api-ref/Zone/list#List) request. ||
|| subnetId | **string**

ID of the subnet to assign to the host.

This subnet should be a part of the cluster network (the network ID is specified in the [ClusterService.CreateClusterRequest.networkId](/docs/managed-mysql/api-ref/Cluster/create#yandex.cloud.mdb.mysql.v1.CreateClusterRequest)). ||
|| assignPublicIp | **boolean**

Option that enables public IP address for the host so that the host can be accessed from the internet.

After a host has been created, this setting cannot be changed.
To remove an assigned public IP address, or to assign a public IP address to a host without one, recreate the host with the appropriate `assignPublicIp` value set.

Possible values:
* `false` - don't assign a public IP address to the host.
* `true` - assign a public IP address to the host. ||
|| replicationSource | **string**

[Host.name](/docs/managed-mysql/api-ref/Cluster/listHosts#yandex.cloud.mdb.mysql.v1.Host) of the host to be used as the replication source (for cascading replication). ||
|| backupPriority | **string** (int64)

Host backup priority ||
|| priority | **string** (int64)

Host master promotion priority ||
|#

## Response {#yandex.cloud.operation.Operation}

**HTTP Code: 200 - OK**

```json
{
  "id": "string",
  "description": "string",
  "createdAt": "string",
  "createdBy": "string",
  "modifiedAt": "string",
  "done": "boolean",
  "metadata": {
    "clusterId": "string",
    "hostNames": [
      "string"
    ]
  },
  // Includes only one of the fields `error`
  "error": {
    "code": "integer",
    "message": "string",
    "details": [
      "object"
    ]
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
|| createdAt | **string** (date-time)

Creation timestamp.

String in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) text format. The range of possible values is from
`0001-01-01T00:00:00Z` to `9999-12-31T23:59:59.999999999Z`, i.e. from 0 to 9 digits for fractions of a second.

To work with values in this field, use the APIs described in the
[Protocol Buffers reference](https://developers.google.com/protocol-buffers/docs/reference/overview).
In some languages, built-in datetime utilities do not support nanosecond precision (9 digits). ||
|| createdBy | **string**

ID of the user or service account who initiated the operation. ||
|| modifiedAt | **string** (date-time)

The time when the Operation resource was last modified.

String in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) text format. The range of possible values is from
`0001-01-01T00:00:00Z` to `9999-12-31T23:59:59.999999999Z`, i.e. from 0 to 9 digits for fractions of a second.

To work with values in this field, use the APIs described in the
[Protocol Buffers reference](https://developers.google.com/protocol-buffers/docs/reference/overview).
In some languages, built-in datetime utilities do not support nanosecond precision (9 digits). ||
|| done | **boolean**

If the value is `false`, it means the operation is still in progress.
If `true`, the operation is completed, and either `error` or `response` is available. ||
|| metadata | **[AddClusterHostsMetadata](#yandex.cloud.mdb.mysql.v1.AddClusterHostsMetadata)**

Service-specific metadata associated with the operation.
It typically contains the ID of the target resource that the operation is performed on.
Any method that returns a long-running operation should document the metadata type, if any. ||
|| error | **[Status](#google.rpc.Status)**

The error result of the operation in case of failure or cancellation.

Includes only one of the fields `error`.

The operation result.
If `done == false` and there was no failure detected, neither `error` nor `response` is set.
If `done == false` and there was a failure detected, `error` is set.
If `done == true`, exactly one of `error` or `response` is set. ||
|#

## AddClusterHostsMetadata {#yandex.cloud.mdb.mysql.v1.AddClusterHostsMetadata}

#|
||Field | Description ||
|| clusterId | **string**

ID of the cluster to which the hosts are being added. ||
|| hostNames[] | **string**

Names of hosts that are being added. ||
|#

## Status {#google.rpc.Status}

The error result of the operation in case of failure or cancellation.

#|
||Field | Description ||
|| code | **integer** (int32)

Error code. An enum value of [google.rpc.Code](https://github.com/googleapis/googleapis/blob/master/google/rpc/code.proto). ||
|| message | **string**

An error message. ||
|| details[] | **object**

A list of messages that carry the error details. ||
|#