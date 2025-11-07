# Introduction to Crypto Architecture Kit

The Crypto Architecture Kit provides functionalities related to encryption/decryption, signature/verification, message authentication codes, hashing, secure random number generation, key derivation, and more.

By abstracting the implementation differences of third-party cryptographic algorithm libraries, the Crypto Architecture Kit offers a unified algorithmic framework. Developers can invoke the encryption/decryption algorithm framework services while ignoring the discrepancies among underlying third-party algorithm libraries, enabling rapid development.

## Basic Concepts

Before developing specific functionalities, developers should familiarize themselves with the following fundamental concepts.

- Symmetric Key

  Both encryption and decryption parties use the same key pair to perform data encryption and decryption operations. Specifically, the data sender employs a specific encryption key to process plaintext through a specialized encryption algorithm, transforming it into complex ciphertext for transmission. The receiver must use the same key and the inverse algorithm to decrypt the ciphertext and restore the original readable plaintext.

- Asymmetric Key

  Asymmetric keys utilize two distinct keys—a public key and a private key—for algorithmic operations. The public key is openly shared, while the private key remains confidential.

  For encryption/decryption operations, the public key is typically used to encrypt plaintext into ciphertext, which can then be decrypted only by the holder of the corresponding private key.

  For signature/verification operations, the private key is used to sign plaintext. Holders of the public key can then verify the signature data to confirm whether the data has been tampered with.

## Capabilities

The cryptographic algorithm library provides developers with the following functionalities, along with corresponding algorithm specifications and development guidelines. Developers should refer to these resources during implementation.

- [Key Generation and Conversion](./cj-crypto-key-generation-conversion-overview.md)
- [Encryption/Decryption](./cj-crypto-encryption-decryption-overview.md)
- [Message Digest Calculation](./cj-crypto-generate-message-digest-overview.md)
- [Message Authentication Code Calculation](./cj-crypto-compute-mac.md)
- [Secure Random Number Generation](./cj-crypto-generate-random-number.md)

## Relationship with Related Kits

The cryptographic algorithm library framework solely offers cryptographic operations for keys and does not include key management functionalities. Consequently, when using the algorithm library, applications must manage their own key storage. This is suitable for scenarios involving temporary session keys that reside only in memory or where applications implement their own secure key storage solutions.

For scenarios requiring system-provided key management functionalities (e.g., key storage), refer to [Universal Keystore Kit (Key Management Service)](../UniversalKeystoreKit/cj-huks-overview.md).

## Constraints and Limitations

- The Crypto Architecture Kit does not support concurrent multi-threaded operations.
- Currently, the Crypto Architecture Kit only supports OpenSSL.
- While the Crypto Architecture Kit provides most commonly used algorithms, certain algorithms and specifications (e.g., MD5) are not suitable for high-security scenarios. Developers should select appropriate algorithms based on actual requirements.