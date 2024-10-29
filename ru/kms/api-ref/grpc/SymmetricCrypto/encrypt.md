---
editable: false
sourcePath: en/_api-ref-grpc/kms/v1/api-ref/grpc/SymmetricCrypto/encrypt.md
---

# Key Management Service API, gRPC: SymmetricCryptoService.Encrypt {#Encrypt}

Encrypts given plaintext with the specified key.

## gRPC request

**rpc Encrypt ([SymmetricEncryptRequest](#yandex.cloud.kms.v1.SymmetricEncryptRequest)) returns ([SymmetricEncryptResponse](#yandex.cloud.kms.v1.SymmetricEncryptResponse))**

## SymmetricEncryptRequest {#yandex.cloud.kms.v1.SymmetricEncryptRequest}

```json
{
  "keyId": "string",
  "versionId": "string",
  "aadContext": "bytes",
  "plaintext": "bytes"
}
```

#|
||Field | Description ||
|| keyId | **string**

Required field. ID of the symmetric KMS key to use for encryption. ||
|| versionId | **string**

ID of the key version to encrypt plaintext with.
Defaults to the primary version if not specified. ||
|| aadContext | **bytes**

Additional authenticated data (AAD context), optional.
If specified, this data will be required for decryption with the [SymmetricDecryptRequest](/docs/kms/api-ref/grpc/SymmetricCrypto/decrypt#yandex.cloud.kms.v1.SymmetricDecryptRequest).
Should be encoded with base64. ||
|| plaintext | **bytes**

Required field. Plaintext to be encrypted.
Should be encoded with base64. ||
|#

## SymmetricEncryptResponse {#yandex.cloud.kms.v1.SymmetricEncryptResponse}

```json
{
  "keyId": "string",
  "versionId": "string",
  "ciphertext": "bytes"
}
```

#|
||Field | Description ||
|| keyId | **string**

Required field. ID of the symmetric KMS key that was used for encryption. ||
|| versionId | **string**

ID of the key version that was used for encryption. ||
|| ciphertext | **bytes**

Resulting ciphertext. ||
|#