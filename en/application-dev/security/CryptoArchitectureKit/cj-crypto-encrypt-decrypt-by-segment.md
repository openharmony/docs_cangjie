# Segment Encryption and Decryption Instructions

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

During the encryption and decryption process, the algorithm library does not impose size limits on single or cumulative data input. However, when processing large data volumes (e.g., exceeding 2MB), developers are advised to segment the data and perform segmented encryption/decryption for improved efficiency.

## Symmetric Encryption and Decryption

For symmetric key segmented encryption/decryption, implement it by calling the [update](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-updatedatablob) function.

Developers can customize the data volume per transmission (updateLength in the example) and pass data through multiple calls to the update interface.

The current maximum supported length per transmission is INT_MAX (maximum length of Uint8Array type).

**Development Example:** [Segmented AES Symmetric Key Encryption/Decryption (GCM Mode)](./cj-crypto-aes-sym-encrypt-decrypt-gcm-by-segment.md)

**Development Example:** [Segmented SM4 Symmetric Key Encryption/Decryption (GCM Mode)](./cj-crypto-sm4-sym-encrypt-decrypt-gcm-by-segment.md)

## Asymmetric Encryption and Decryption

Asymmetric encryption/decryption does not support update operations. Only the [init](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-initcryptomode-key-paramsspec) function needs to be called to complete the process.

Segmented encryption with asymmetric keys refers to situations where plaintext exceeds the single-encryption data length limit (specific lengths can be found in [Asymmetric Key Encryption/Decryption Specifications](./cj-crypto-asym-encrypt-decrypt-spec.md)). In such cases, the data to be encrypted must be divided into appropriately sized segments, with each segment undergoing separate encryption operations—i.e., creating a Cipher object and calling the [init](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-initcryptomode-key-paramsspec) interface.

Strictly speaking, this constitutes split-data encryption/decryption, where the length of data per transmission depends on the key specifications.

- **RSA**: Different padding modes impose different data input rules. Refer to [RSA Algorithm Specifications](./cj-crypto-asym-encrypt-decrypt-spec.md#rsa) to determine the permissible data length per transmission.
- **SM2**: Encryption length must adhere to fixed-length requirements. Details can be found in [SM2 Algorithm Specifications](./cj-crypto-asym-encrypt-decrypt-spec.md#sm2).

## Frequently Asked Questions

In segmented encryption/decryption, is the data volume per update related to the encryption mode?

   The data volume per update is developer-defined and independent of the encryption mode.

   Different encryption modes only affect cryptographic parameters. Each mode uses distinct parameters, as specified in [ParamsSpec](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#interface-paramsspec).