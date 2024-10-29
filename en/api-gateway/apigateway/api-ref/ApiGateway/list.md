---
editable: false
sourcePath: en/_api-ref/serverless/apigateway/v1/apigateway/api-ref/ApiGateway/list.md
---

# API Gateway Service, REST: ApiGateway.List {#List}

Retrieves the list of API gateways in the specified folder.

## HTTP request

```
GET https://serverless-apigateway.{{ api-host }}/apigateways/v1/apigateways
```

## Query parameters {#yandex.cloud.serverless.apigateway.v1.ListApiGatewayRequest}

#|
||Field | Description ||
|| folderId | **string**

Required field. ID of the folder to list API gateways in.

To get a folder ID make a [yandex.cloud.resourcemanager.v1.FolderService.List](/docs/resource-manager/api-ref/Folder/list#List) request. ||
|| pageSize | **string** (int64)

The maximum number of results per page to return. If the number of available
results is larger than `pageSize`, the service returns a [ListApiGatewayResponse.nextPageToken](#yandex.cloud.serverless.apigateway.v1.ListApiGatewayResponse)
that can be used to get the next page of results in subsequent list requests.

Default value: 100. ||
|| pageToken | **string**

Page token. To get the next page of results, set `pageToken` to the
[ListApiGatewayResponse.nextPageToken](#yandex.cloud.serverless.apigateway.v1.ListApiGatewayResponse) returned by a previous list request. ||
|| filter | **string**

A filter expression that filters functions listed in the response.

The expression must specify:
1. The field name. Currently filtering can only be applied to the [ApiGateway.name](index) field.
2. An `=` operator.
3. The value in double quotes (`"`). Must be 3-63 characters long and match the regular expression `[a-z]([-a-z0-9]{0,61}[a-z0-9])?`.
Example of a filter: `name=my-apigw`. ||
|#

## Response {#yandex.cloud.serverless.apigateway.v1.ListApiGatewayResponse}

**HTTP Code: 200 - OK**

```json
{
  "apiGateways": [
    {
      "id": "string",
      "folderId": "string",
      "createdAt": "string",
      "name": "string",
      "description": "string",
      "labels": "string",
      "status": "string",
      "domain": "string",
      "logGroupId": "string",
      "attachedDomains": [
        {
          "domainId": "string",
          "certificateId": "string",
          "enabled": "boolean",
          "domain": "string"
        }
      ],
      "connectivity": {
        "networkId": "string",
        "subnetId": [
          "string"
        ]
      },
      "logOptions": {
        "disabled": "boolean",
        // Includes only one of the fields `logGroupId`, `folderId`
        "logGroupId": "string",
        "folderId": "string",
        // end of the list of possible fields
        "minLevel": "string"
      },
      "variables": {
        // Includes only one of the fields `stringValue`, `intValue`, `doubleValue`, `boolValue`
        "stringValue": "string",
        "intValue": "string",
        "doubleValue": "string",
        "boolValue": "boolean"
        // end of the list of possible fields
      },
      "canary": {
        "weight": "string",
        "variables": {
          // Includes only one of the fields `stringValue`, `intValue`, `doubleValue`, `boolValue`
          "stringValue": "string",
          "intValue": "string",
          "doubleValue": "string",
          "boolValue": "boolean"
          // end of the list of possible fields
        }
      },
      "executionTimeout": "string"
    }
  ],
  "nextPageToken": "string"
}
```

#|
||Field | Description ||
|| apiGateways[] | **[ApiGateway](#yandex.cloud.serverless.apigateway.v1.ApiGateway)**

List of API gateways in the specified folder. ||
|| nextPageToken | **string**

Token for getting the next page of the list. If the number of results is greater than
the specified [ListApiGatewayRequest.pageSize](#yandex.cloud.serverless.apigateway.v1.ListApiGatewayRequest), use `nextPageToken` as the value
for the [ListApiGatewayRequest.pageToken](#yandex.cloud.serverless.apigateway.v1.ListApiGatewayRequest) parameter in the next list request.

Each subsequent page will have its own `nextPageToken` to continue paging through the results. ||
|#

## ApiGateway {#yandex.cloud.serverless.apigateway.v1.ApiGateway}

#|
||Field | Description ||
|| id | **string**

ID of the API gateway. Generated at creation time. ||
|| folderId | **string**

ID of the folder that the API gateway belongs to. ||
|| createdAt | **string** (date-time)

Creation timestamp for the API-gateway.

String in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) text format. The range of possible values is from
`0001-01-01T00:00:00Z` to `9999-12-31T23:59:59.999999999Z`, i.e. from 0 to 9 digits for fractions of a second.

To work with values in this field, use the APIs described in the
[Protocol Buffers reference](https://developers.google.com/protocol-buffers/docs/reference/overview).
In some languages, built-in datetime utilities do not support nanosecond precision (9 digits). ||
|| name | **string**

Name of the API gateway. The name is unique within the folder. ||
|| description | **string**

Description of the API gateway. ||
|| labels | **string**

API gateway labels as `key:value` pairs. ||
|| status | **enum** (Status)

Status of the API gateway.

- `STATUS_UNSPECIFIED`
- `CREATING`: API gateway is being created.
- `ACTIVE`: API gateway is ready for use.
- `DELETING`: API gateway is being deleted.
- `ERROR`: API gateway failed. The only allowed action is delete.
- `UPDATING`: API gateway is being updated. ||
|| domain | **string**

Default domain for the API gateway. Generated at creation time. ||
|| logGroupId | **string**

ID of the log group for the API gateway. ||
|| attachedDomains[] | **[AttachedDomain](#yandex.cloud.serverless.apigateway.v1.AttachedDomain)**

List of domains attached to API gateway. ||
|| connectivity | **[Connectivity](#yandex.cloud.serverless.apigateway.v1.Connectivity)**

Network access. If specified the gateway will be attached to specified network/subnet(s). ||
|| logOptions | **[LogOptions](#yandex.cloud.serverless.apigateway.v1.LogOptions)**

Options for logging from the API gateway. ||
|| variables | **[VariableInput](#yandex.cloud.serverless.apigateway.v1.VariableInput)**

Values of variables defined in the specification. ||
|| canary | **[Canary](#yandex.cloud.serverless.apigateway.v1.Canary)**

Canary release of the gateway. ||
|| executionTimeout | **string** (duration)

Timeout for gateway call execution ||
|#

## AttachedDomain {#yandex.cloud.serverless.apigateway.v1.AttachedDomain}

#|
||Field | Description ||
|| domainId | **string**

ID of the domain. ||
|| certificateId | **string**

ID of the domain certificate. ||
|| enabled | **boolean**

Enabling flag. ||
|| domain | **string**

Name of the domain. ||
|#

## Connectivity {#yandex.cloud.serverless.apigateway.v1.Connectivity}

Gateway connectivity specification.

#|
||Field | Description ||
|| networkId | **string**

Network the gateway will have access to.
It's essential to specify network with subnets in all availability zones. ||
|| subnetId[] | **string**

Complete list of subnets (from the same network) the gateway can be attached to.
It's essential to specify at least one subnet for each availability zones. ||
|#

## LogOptions {#yandex.cloud.serverless.apigateway.v1.LogOptions}

#|
||Field | Description ||
|| disabled | **boolean**

Is logging from API gateway disabled. ||
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

## VariableInput {#yandex.cloud.serverless.apigateway.v1.VariableInput}

#|
||Field | Description ||
|| stringValue | **string**

Includes only one of the fields `stringValue`, `intValue`, `doubleValue`, `boolValue`.

Variable value that can has only primitive type ||
|| intValue | **string** (int64)

Includes only one of the fields `stringValue`, `intValue`, `doubleValue`, `boolValue`.

Variable value that can has only primitive type ||
|| doubleValue | **string**

Includes only one of the fields `stringValue`, `intValue`, `doubleValue`, `boolValue`.

Variable value that can has only primitive type ||
|| boolValue | **boolean**

Includes only one of the fields `stringValue`, `intValue`, `doubleValue`, `boolValue`.

Variable value that can has only primitive type ||
|#

## Canary {#yandex.cloud.serverless.apigateway.v1.Canary}

#|
||Field | Description ||
|| weight | **string** (int64)

It describes percentage of requests, which will be processed by canary. ||
|| variables | **[VariableInput](#yandex.cloud.serverless.apigateway.v1.VariableInput)**

Values specification variables, associated with canary. ||
|#