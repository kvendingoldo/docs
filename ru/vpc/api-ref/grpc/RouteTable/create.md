---
editable: false
sourcePath: en/_api-ref-grpc/vpc/v1/api-ref/grpc/RouteTable/create.md
---

# Virtual Private Cloud API, gRPC: RouteTableService.Create {#Create}

Creates a route table in the specified folder and network.
Method starts an asynchronous operation that can be cancelled while it is in progress.

## gRPC request

**rpc Create ([CreateRouteTableRequest](#yandex.cloud.vpc.v1.CreateRouteTableRequest)) returns ([operation.Operation](#yandex.cloud.operation.Operation))**

## CreateRouteTableRequest {#yandex.cloud.vpc.v1.CreateRouteTableRequest}

```json
{
  "folderId": "string",
  "name": "string",
  "description": "string",
  "labels": "string",
  "networkId": "string",
  "staticRoutes": [
    {
      // Includes only one of the fields `destinationPrefix`
      "destinationPrefix": "string",
      // end of the list of possible fields
      // Includes only one of the fields `nextHopAddress`, `gatewayId`
      "nextHopAddress": "string",
      "gatewayId": "string",
      // end of the list of possible fields
      "labels": "string"
    }
  ]
}
```

#|
||Field | Description ||
|| folderId | **string**

Required field. ID of the folder that the route table belongs to.
To get the folder ID use a [yandex.cloud.resourcemanager.v1.FolderService.List](/docs/resource-manager/api-ref/grpc/Folder/list#List) request. ||
|| name | **string**

Name of the route table.
The name must be unique within the folder. ||
|| description | **string**

Description of the route table. ||
|| labels | **string**

Resource labels, `` key:value `` pairs. ||
|| networkId | **string**

Required field. ID of the network the route table belongs to. ||
|| staticRoutes[] | **[StaticRoute](#yandex.cloud.vpc.v1.StaticRoute)**

List of static routes. ||
|#

## StaticRoute {#yandex.cloud.vpc.v1.StaticRoute}

A StaticRoute resource. For more information, see [Static Routes](/docs/vpc/concepts/routing).

#|
||Field | Description ||
|| destinationPrefix | **string**

Destination subnet in CIDR notation

Includes only one of the fields `destinationPrefix`. ||
|| nextHopAddress | **string**

Next hop IP address

Includes only one of the fields `nextHopAddress`, `gatewayId`. ||
|| gatewayId | **string**

Next hop gateway id

Includes only one of the fields `nextHopAddress`, `gatewayId`. ||
|| labels | **string**

Resource labels as `` key:value `` pairs. Maximum of 64 per resource. ||
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
    "routeTableId": "string"
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
    "networkId": "string",
    "staticRoutes": [
      {
        // Includes only one of the fields `destinationPrefix`
        "destinationPrefix": "string",
        // end of the list of possible fields
        // Includes only one of the fields `nextHopAddress`, `gatewayId`
        "nextHopAddress": "string",
        "gatewayId": "string",
        // end of the list of possible fields
        "labels": "string"
      }
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
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp. ||
|| createdBy | **string**

ID of the user or service account who initiated the operation. ||
|| modifiedAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

The time when the Operation resource was last modified. ||
|| done | **bool**

If the value is `false`, it means the operation is still in progress.
If `true`, the operation is completed, and either `error` or `response` is available. ||
|| metadata | **[CreateRouteTableMetadata](#yandex.cloud.vpc.v1.CreateRouteTableMetadata)**

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
|| response | **[RouteTable](#yandex.cloud.vpc.v1.RouteTable)**

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

## CreateRouteTableMetadata {#yandex.cloud.vpc.v1.CreateRouteTableMetadata}

#|
||Field | Description ||
|| routeTableId | **string**

ID of the route table that is being created. ||
|#

## RouteTable {#yandex.cloud.vpc.v1.RouteTable}

A RouteTable resource. For more information, see [Static Routes](/docs/vpc/concepts/routing).

#|
||Field | Description ||
|| id | **string**

ID of the route table. ||
|| folderId | **string**

ID of the folder that the route table belongs to. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) text format. ||
|| name | **string**

Name of the route table.
The name must be unique within the folder.
Value must match the regular expression `\|[a-zA-Z]([-_a-zA-Z0-9]{0,61}[a-zA-Z0-9])?`. ||
|| description | **string**

Optional description of the route table. 0-256 characters long. ||
|| labels | **string**

Resource labels, `key:value` pairs.
No more than 64 per resource.
The string length in characters for each key must be 1-63.
Each value must match the regular expression `[-_0-9a-z]*`.
Each key must match the regular expression `[a-z][-_0-9a-z]*`. ||
|| networkId | **string**

ID of the network the route table belongs to. ||
|| staticRoutes[] | **[StaticRoute](#yandex.cloud.vpc.v1.StaticRoute2)**

List of static routes. ||
|#

## StaticRoute {#yandex.cloud.vpc.v1.StaticRoute2}

A StaticRoute resource. For more information, see [Static Routes](/docs/vpc/concepts/routing).

#|
||Field | Description ||
|| destinationPrefix | **string**

Destination subnet in CIDR notation

Includes only one of the fields `destinationPrefix`. ||
|| nextHopAddress | **string**

Next hop IP address

Includes only one of the fields `nextHopAddress`, `gatewayId`. ||
|| gatewayId | **string**

Next hop gateway id

Includes only one of the fields `nextHopAddress`, `gatewayId`. ||
|| labels | **string**

Resource labels as `` key:value `` pairs. Maximum of 64 per resource. ||
|#