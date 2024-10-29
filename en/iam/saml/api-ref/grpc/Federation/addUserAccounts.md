---
editable: false
sourcePath: en/_api-ref-grpc/iam/v1/saml/api-ref/grpc/Federation/addUserAccounts.md
---

# Identity and Access Management SAML API, gRPC: FederationService.AddUserAccounts {#AddUserAccounts}

Adds users to the specified federation.

## gRPC request

**rpc AddUserAccounts ([AddFederatedUserAccountsRequest](#yandex.cloud.iam.v1.saml.AddFederatedUserAccountsRequest)) returns ([operation.Operation](#yandex.cloud.operation.Operation))**

## AddFederatedUserAccountsRequest {#yandex.cloud.iam.v1.saml.AddFederatedUserAccountsRequest}

```json
{
  "federationId": "string",
  "nameIds": [
    "string"
  ]
}
```

#|
||Field | Description ||
|| federationId | **string**

ID of the federation to add users. ||
|| nameIds[] | **string**

Name IDs returned by the Identity Provider (IdP) on successful authentication.
These may be UPNs or user email addresses. ||
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
    "federationId": "string"
  },
  // Includes only one of the fields `error`, `response`
  "error": "google.rpc.Status",
  "response": {
    "userAccounts": [
      {
        "id": "string",
        // Includes only one of the fields `yandexPassportUserAccount`, `samlUserAccount`
        "yandexPassportUserAccount": {
          "login": "string",
          "defaultEmail": "string"
        },
        "samlUserAccount": {
          "federationId": "string",
          "nameId": "string",
          "attributes": {
            "value": [
              "string"
            ]
          }
        }
        // end of the list of possible fields
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
|| metadata | **[AddFederatedUserAccountsMetadata](#yandex.cloud.iam.v1.saml.AddFederatedUserAccountsMetadata)**

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
|| response | **[AddFederatedUserAccountsResponse](#yandex.cloud.iam.v1.saml.AddFederatedUserAccountsResponse)**

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

## AddFederatedUserAccountsMetadata {#yandex.cloud.iam.v1.saml.AddFederatedUserAccountsMetadata}

#|
||Field | Description ||
|| federationId | **string**

ID of the federation that is being altered. ||
|#

## AddFederatedUserAccountsResponse {#yandex.cloud.iam.v1.saml.AddFederatedUserAccountsResponse}

#|
||Field | Description ||
|| userAccounts[] | **[UserAccount](#yandex.cloud.iam.v1.UserAccount)**

List of users created by [FederationService.AddUserAccounts](#AddUserAccounts) request. ||
|#

## UserAccount {#yandex.cloud.iam.v1.UserAccount}

Currently represents only [Yandex account](/docs/iam/concepts/#passport).

#|
||Field | Description ||
|| id | **string**

ID of the user account. ||
|| yandexPassportUserAccount | **[YandexPassportUserAccount](#yandex.cloud.iam.v1.YandexPassportUserAccount)**

A YandexPassportUserAccount resource.

Includes only one of the fields `yandexPassportUserAccount`, `samlUserAccount`. ||
|| samlUserAccount | **[SamlUserAccount](#yandex.cloud.iam.v1.SamlUserAccount)**

A SAML federated user.

Includes only one of the fields `yandexPassportUserAccount`, `samlUserAccount`. ||
|#

## YandexPassportUserAccount {#yandex.cloud.iam.v1.YandexPassportUserAccount}

A YandexPassportUserAccount resource.
For more information, see [Yandex account](/docs/iam/concepts/#passport).

#|
||Field | Description ||
|| login | **string**

Login of the Yandex user account. ||
|| defaultEmail | **string**

Default email of the Yandex user account. ||
|#

## SamlUserAccount {#yandex.cloud.iam.v1.SamlUserAccount}

A SAML federated user.
For more information, see [federations](/docs/iam/concepts/federations).

#|
||Field | Description ||
|| federationId | **string**

Required field. ID of the federation that the federation belongs to. ||
|| nameId | **string**

Required field. Name Id of the SAML federated user.
The name is unique within the federation. 1-256 characters long. ||
|| attributes | **[Attribute](#yandex.cloud.iam.v1.SamlUserAccount.Attribute)**

Additional attributes of the SAML federated user. ||
|#

## Attribute {#yandex.cloud.iam.v1.SamlUserAccount.Attribute}

#|
||Field | Description ||
|| value[] | **string** ||
|#