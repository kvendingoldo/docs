---
editable: false
sourcePath: en/_api-ref-grpc/certificatemanager/v1/api-ref/grpc/Certificate/list.md
---

# Certificate Manager API, gRPC: CertificateService.List {#List}

Returns the list of certificates in the specified folder.

## gRPC request

**rpc List ([ListCertificatesRequest](#yandex.cloud.certificatemanager.v1.ListCertificatesRequest)) returns ([ListCertificatesResponse](#yandex.cloud.certificatemanager.v1.ListCertificatesResponse))**

## ListCertificatesRequest {#yandex.cloud.certificatemanager.v1.ListCertificatesRequest}

```json
{
  "folderId": "string",
  "pageSize": "int64",
  "pageToken": "string",
  "view": "CertificateView"
}
```

#|
||Field | Description ||
|| folderId | **string**

Required field. ID of the folder to list certificate in. ||
|| pageSize | **int64**

The maximum number of results per page to return. If the number of available
results is larger than `page_size`, the service returns a [ListCertificatesResponse.nextPageToken](#yandex.cloud.certificatemanager.v1.ListCertificatesResponse)
that can be used to get the next page of results in subsequent list requests.
Default value: 100. ||
|| pageToken | **string**

Page token. To get the next page of results, set `page_token` to the
[ListCertificatesResponse.nextPageToken](#yandex.cloud.certificatemanager.v1.ListCertificatesResponse) returned by a previous list request. ||
|| view | enum **CertificateView**

The output type of the certificate.

- `BASIC`: Output basic information about the certificate.
- `FULL`: Output full information about the certificate including domain challenges. ||
|#

## ListCertificatesResponse {#yandex.cloud.certificatemanager.v1.ListCertificatesResponse}

```json
{
  "certificates": [
    {
      "id": "string",
      "folderId": "string",
      "createdAt": "google.protobuf.Timestamp",
      "name": "string",
      "description": "string",
      "labels": "string",
      "type": "CertificateType",
      "domains": [
        "string"
      ],
      "status": "Status",
      "issuer": "string",
      "subject": "string",
      "serial": "string",
      "updatedAt": "google.protobuf.Timestamp",
      "issuedAt": "google.protobuf.Timestamp",
      "notAfter": "google.protobuf.Timestamp",
      "notBefore": "google.protobuf.Timestamp",
      "challenges": [
        {
          "domain": "string",
          "type": "ChallengeType",
          "createdAt": "google.protobuf.Timestamp",
          "updatedAt": "google.protobuf.Timestamp",
          "status": "Status",
          "message": "string",
          "error": "string",
          // Includes only one of the fields `dnsChallenge`, `httpChallenge`
          "dnsChallenge": {
            "name": "string",
            "type": "string",
            "value": "string"
          },
          "httpChallenge": {
            "url": "string",
            "content": "string"
          }
          // end of the list of possible fields
        }
      ],
      "deletionProtection": "bool",
      "incompleteChain": "bool"
    }
  ],
  "nextPageToken": "string"
}
```

#|
||Field | Description ||
|| certificates[] | **[Certificate](#yandex.cloud.certificatemanager.v1.Certificate)**

List of certificates in the specified folder. ||
|| nextPageToken | **string**

This token allows you to get the next page of results for list requests. If the number
of results is greater than the specified [ListCertificatesRequest.pageSize](#yandex.cloud.certificatemanager.v1.ListCertificatesRequest), use
the `next_page_token` as the value for the [ListCertificatesRequest.pageToken](#yandex.cloud.certificatemanager.v1.ListCertificatesRequest) query parameter
in the next list request. Each subsequent list request will have its own
`nextPageToken` to continue paging through the results. ||
|#

## Certificate {#yandex.cloud.certificatemanager.v1.Certificate}

A certificate. For details about the concept, see [documentation](/docs/certificate-manager/concepts/).

#|
||Field | Description ||
|| id | **string**

ID of the certificate. Generated at creation time. ||
|| folderId | **string**

ID of the folder that the certificate belongs to. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp. ||
|| name | **string**

Name of the certificate.
The name is unique within the folder. ||
|| description | **string**

Description of the certificate. ||
|| labels | **string**

Certificate labels as `key:value` pairs. ||
|| type | enum **CertificateType**

Type of the certificate.

- `CERTIFICATE_TYPE_UNSPECIFIED`
- `IMPORTED`: The certificate is imported by user.
- `MANAGED`: The certificate is created by service. ||
|| domains[] | **string**

Fully qualified domain names of the certificate. ||
|| status | enum **Status**

Status of the certificate.

- `STATUS_UNSPECIFIED`
- `VALIDATING`: The certificate domains validation are required. Used only for managed certificates.
- `INVALID`: The certificate issuance is failed. Used only for managed certificates.
- `ISSUED`: The certificate is issued.
- `REVOKED`: The certificate is revoked.
- `RENEWING`: The certificate renewal is started. Used only for managed certificates.
- `RENEWAL_FAILED`: The certificate renewal is failed. Used only for managed certificates. ||
|| issuer | **string**

[Distinguished Name](https://tools.ietf.org/html/rfc1779) of the certificate authority that issued the certificate. ||
|| subject | **string**

[Distinguished Name](https://tools.ietf.org/html/rfc1779) of the entity that is associated with the public key contained in the certificate. ||
|| serial | **string**

Serial number of the certificate. ||
|| updatedAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Time when the certificate is updated. ||
|| issuedAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Time when the certificate is issued. ||
|| notAfter | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Time after which the certificate is not valid. ||
|| notBefore | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Time before which the certificate is not valid. ||
|| challenges[] | **[Challenge](#yandex.cloud.certificatemanager.v1.Challenge)**

Domains validation challenges of the certificate. Used only for managed certificates. ||
|| deletionProtection | **bool**

Flag that protects deletion of the certificate ||
|| incompleteChain | **bool**

Mark imported certificates without uploaded chain or with chain which not lead to root certificate ||
|#

## Challenge {#yandex.cloud.certificatemanager.v1.Challenge}

Domain validation challenge.

#|
||Field | Description ||
|| domain | **string**

Domain of the challenge. ||
|| type | enum **ChallengeType**

Type of the challenge.

- `CHALLENGE_TYPE_UNSPECIFIED`
- `DNS`: Domain validation type that using DNS-records.
- `HTTP`: Domain validation type that using HTTP-files. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Time when the challenge is created. ||
|| updatedAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Time when the challenge is updated. ||
|| status | enum **Status**

Status of the challenge.

- `STATUS_UNSPECIFIED`
- `PENDING`: The challenge is waiting to be completed.
- `PROCESSING`: The challenge is awaiting approval from Let's Encrypt.
- `VALID`: The challenge is complete.
- `INVALID`: The rights check for a specific domain failed or the one-week period allocated for the check expired. ||
|| message | **string**

Description of the challenge. ||
|| error | **string**

Error of the challenge. ||
|| dnsChallenge | **[DnsRecord](#yandex.cloud.certificatemanager.v1.Challenge.DnsRecord)**

DNS-record.

Includes only one of the fields `dnsChallenge`, `httpChallenge`.

Data of the challenge. ||
|| httpChallenge | **[HttpFile](#yandex.cloud.certificatemanager.v1.Challenge.HttpFile)**

HTTP-file.

Includes only one of the fields `dnsChallenge`, `httpChallenge`.

Data of the challenge. ||
|#

## DnsRecord {#yandex.cloud.certificatemanager.v1.Challenge.DnsRecord}

#|
||Field | Description ||
|| name | **string**

Name of the DNS record. ||
|| type | **string**

Type of the DNS-record. ||
|| value | **string**

Value of the DNS-record. ||
|#

## HttpFile {#yandex.cloud.certificatemanager.v1.Challenge.HttpFile}

#|
||Field | Description ||
|| url | **string**

Location of the HTTP file. ||
|| content | **string**

Content of the HTTP file. ||
|#