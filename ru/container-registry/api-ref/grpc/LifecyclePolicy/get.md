---
editable: false
sourcePath: en/_api-ref-grpc/containerregistry/v1/api-ref/grpc/LifecyclePolicy/get.md
---

# Container Registry API, gRPC: LifecyclePolicyService.Get {#Get}

Returns the specified lifecycle policy.

To get the list of all available lifecycle policies, make a [List](/docs/container-registry/api-ref/grpc/LifecyclePolicy/list#List) request.

## gRPC request

**rpc Get ([GetLifecyclePolicyRequest](#yandex.cloud.containerregistry.v1.GetLifecyclePolicyRequest)) returns ([LifecyclePolicy](#yandex.cloud.containerregistry.v1.LifecyclePolicy))**

## GetLifecyclePolicyRequest {#yandex.cloud.containerregistry.v1.GetLifecyclePolicyRequest}

```json
{
  "lifecyclePolicyId": "string"
}
```

#|
||Field | Description ||
|| lifecyclePolicyId | **string**

Required field. ID of the lifecycle policy. ||
|#

## LifecyclePolicy {#yandex.cloud.containerregistry.v1.LifecyclePolicy}

```json
{
  "id": "string",
  "name": "string",
  "repositoryId": "string",
  "description": "string",
  "status": "Status",
  "createdAt": "google.protobuf.Timestamp",
  "rules": [
    {
      "description": "string",
      "expirePeriod": "google.protobuf.Duration",
      "tagRegexp": "string",
      "untagged": "bool",
      "retainedTop": "int64"
    }
  ]
}
```

#|
||Field | Description ||
|| id | **string**

ID of the lifecycle policy. ||
|| name | **string**

Name of the lifecycle policy. ||
|| repositoryId | **string**

ID of the repository that the lifecycle policy belongs to.
Required. The maximum string length in characters is 50. ||
|| description | **string**

Description of the lifecycle policy.
The maximum string length in characters is 256. ||
|| status | enum **Status**

Status of lifecycle policy.

- `STATUS_UNSPECIFIED`
- `ACTIVE`: Policy is active and regularly deletes Docker images according to the established rules.
- `DISABLED`: Policy is disabled and does not delete Docker images in the repository.
Policies in this status can be used for preparing and testing rules. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp. ||
|| rules[] | **[LifecycleRule](#yandex.cloud.containerregistry.v1.LifecycleRule)**

The rules of lifecycle policy. ||
|#

## LifecycleRule {#yandex.cloud.containerregistry.v1.LifecycleRule}

#|
||Field | Description ||
|| description | **string**

Description of the lifecycle policy rule. ||
|| expirePeriod | **[google.protobuf.Duration](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/duration)**

Period of time for automatic deletion.
Period must be a multiple of 24 hours. ||
|| tagRegexp | **string**

Tag for specifying a filter in the form of a regular expression. ||
|| untagged | **bool**

Tag for applying the rule to Docker images without tags. ||
|| retainedTop | **int64**

Number of Docker images (falling under the specified filter by tags) that must be left, even if the expire_period has already expired. ||
|#