---
editable: false
sourcePath: en/_api-ref/mdb/redis/v1/api-ref/Cluster/getShard.md
---

# Managed Service for Redis API, REST: Cluster.GetShard {#GetShard}

Returns the specified shard.

## HTTP request

```
GET https://{{ api-host-mdb }}/managed-redis/v1/clusters/{clusterId}/shards/{shardName}
```

## Path parameters

#|
||Field | Description ||
|| clusterId | **string**

Required field. ID of the Redis cluster the shard belongs to.
To get the cluster ID use a [ClusterService.List](/docs/managed-redis/api-ref/Cluster/list#List) request. ||
|| shardName | **string**

Required field. Name of Redis shard to return.
To get the shard name use a [ClusterService.ListShards](/docs/managed-redis/api-ref/Cluster/listShards#ListShards) request. ||
|#

## Response {#yandex.cloud.mdb.redis.v1.Shard}

**HTTP Code: 200 - OK**

```json
{
  "name": "string",
  "clusterId": "string"
}
```

#|
||Field | Description ||
|| name | **string**

Name of the Redis shard. The shard name is assigned by user at creation time, and cannot be changed.
1-63 characters long. ||
|| clusterId | **string**

ID of the Redis cluster the shard belongs to. The ID is assigned by MDB at creation time. ||
|#