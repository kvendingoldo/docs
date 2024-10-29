---
editable: false
sourcePath: en/_api-ref/cdn/v1/api-ref/OriginGroup/get.md
---

# Cloud CDN API, REST: OriginGroup.Get {#Get}

Gets origin group with specified origin group id.

## HTTP request

```
GET https://cdn.{{ api-host }}/cdn/v1/originGroups/{originGroupId}
```

## Path parameters

#|
||Field | Description ||
|| originGroupId | **string** (int64)

Required field. ID of the origin group to return.

To get a origin group ID, make a [OriginGroupService.List](/docs/cdn/api-ref/OriginGroup/list#List) request. ||
|#

## Query parameters {#yandex.cloud.cdn.v1.GetOriginGroupRequest}

#|
||Field | Description ||
|| folderId | **string**

Required field. ID of the folder that the origin group belongs to. ||
|#

## Response {#yandex.cloud.cdn.v1.OriginGroup}

**HTTP Code: 200 - OK**

```json
{
  "id": "string",
  "folderId": "string",
  "name": "string",
  "useNext": "boolean",
  "origins": [
    {
      "id": "string",
      "originGroupId": "string",
      "source": "string",
      "enabled": "boolean",
      "backup": "boolean",
      "meta": {
        // Includes only one of the fields `common`, `bucket`, `website`, `balancer`
        "common": {
          "name": "string"
        },
        "bucket": {
          "name": "string"
        },
        "website": {
          "name": "string"
        },
        "balancer": {
          "id": "string"
        }
        // end of the list of possible fields
      }
    }
  ]
}
```

Origin group parameters. For details about the concept, see [documentation](/docs/cdn/concepts/origins#groups).

#|
||Field | Description ||
|| id | **string** (int64)

ID of the origin group. Generated at creation time. ||
|| folderId | **string**

ID of the folder that the origin group belongs to. ||
|| name | **string**

Name of the origin group. ||
|| useNext | **boolean**

This option have two possible conditions:
true - the option is active. In case the origin responds with 4XX or 5XX codes,
use the next origin from the list.
false - the option is disabled. ||
|| origins[] | **[Origin](#yandex.cloud.cdn.v1.Origin)**

List of origins. ||
|#

## Origin {#yandex.cloud.cdn.v1.Origin}

An origin. For details about the concept, see [documentation](/docs/cdn/concepts/origins).

#|
||Field | Description ||
|| id | **string** (int64)

ID of the origin. ||
|| originGroupId | **string** (int64)

ID of the parent origin group. ||
|| source | **string**

IP address or Domain name of your origin and the port (if custom).
Used if `meta` variant is `common`. ||
|| enabled | **boolean**

The setting allows to enable or disable an Origin source in the Origins group.

It has two possible values:

True - The origin is enabled and used as a source for the CDN. An origins
group must contain at least one enabled origin.
False - The origin is disabled and the CDN is not using it to pull content. ||
|| backup | **boolean**

Specifies whether the origin is used in its origin group as backup.
A backup origin is used when one of active origins becomes unavailable. ||
|| meta | **[OriginMeta](#yandex.cloud.cdn.v1.OriginMeta)**

Set up origin of the content. ||
|#

## OriginMeta {#yandex.cloud.cdn.v1.OriginMeta}

Origin type. For details about the concept, see [documentation](/docs/cdn/concepts/origins).

#|
||Field | Description ||
|| common | **[OriginNamedMeta](#yandex.cloud.cdn.v1.OriginNamedMeta)**

A server with a domain name linked to it

Includes only one of the fields `common`, `bucket`, `website`, `balancer`.

Type of the origin. ||
|| bucket | **[OriginNamedMeta](#yandex.cloud.cdn.v1.OriginNamedMeta)**

An Object Storage bucket not configured as a static site hosting.

Includes only one of the fields `common`, `bucket`, `website`, `balancer`.

Type of the origin. ||
|| website | **[OriginNamedMeta](#yandex.cloud.cdn.v1.OriginNamedMeta)**

An Object Storage bucket configured as a static site hosting.

Includes only one of the fields `common`, `bucket`, `website`, `balancer`.

Type of the origin. ||
|| balancer | **[OriginBalancerMeta](#yandex.cloud.cdn.v1.OriginBalancerMeta)**

An L7 load balancer from Application Load Balancer.
CDN servers will access the load balancer at one of its IP addresses that must be selected in the origin settings.

Includes only one of the fields `common`, `bucket`, `website`, `balancer`.

Type of the origin. ||
|#

## OriginNamedMeta {#yandex.cloud.cdn.v1.OriginNamedMeta}

Origin info. For details about the concept, see [documentation](/docs/cdn/concepts/origins).

#|
||Field | Description ||
|| name | **string**

Name of the origin. ||
|#

## OriginBalancerMeta {#yandex.cloud.cdn.v1.OriginBalancerMeta}

Application Load Balancer origin info. For details about the concept, see [documentation](/docs/cdn/concepts/origins).

#|
||Field | Description ||
|| id | **string**

ID of the origin. ||
|#