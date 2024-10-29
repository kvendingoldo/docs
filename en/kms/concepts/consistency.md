# Key consistency

The [encrypt](../../kms/api-ref/SymmetricCrypto/encrypt.md), [decrypt](../../kms/api-ref/SymmetricCrypto/decrypt.md), and [reEncrypt](../../kms/api-ref/SymmetricCrypto/reEncrypt.md) REST API methods for the [SymmetricCrypto](../../kms/api-ref/SymmetricCrypto/index.md) resource and the [SymmetricCryptoService/Encrypt](../../kms/api-ref/grpc/SymmetricCrypto/encrypt.md), [SymmetricCryptoService/Decrypt](../../kms/api-ref/grpc/SymmetricCrypto/decrypt.md), and gRPC [SymmetricCryptoService/ReEncrypt](../../kms/api-ref/grpc/SymmetricCrypto/reEncrypt.md) API calls are eventually consistent operations. It takes **up to three hours** for the updates they make to take effect.

[Eventually consistent](https://en.wikipedia.org/wiki/Eventual_consistency) operations require **up to three hours** for the changes to take effect:
* Rotating keys (automatically and manually).
* Changing the primary version of a key.
* Changing the key status to `Inactive`.
* Scheduling a key version for destruction.
* Destroying keys.

[Strongly consistent](https://en.wikipedia.org/wiki/Strong_consistency) operations take effect without delay:
* Creating keys.
* Changing the key status to `Active`.
* Canceling scheduled key version destruction (the version status is `Scheduled For Destruction`).

{% note info %}

To quickly restrict access to a key, revoke the roles required to use the key for encrypting and decrypting data. For more information, see [{#T}](../security/index.md).

{% endnote %}