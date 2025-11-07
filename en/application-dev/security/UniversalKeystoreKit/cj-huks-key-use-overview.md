# Key Usage Introduction and General Process  

## Key Usage Introduction  

To achieve data confidentiality, integrity, and other protections, generated/imported keys can be used to perform cryptographic operations on data, such as:  

- [Encryption and Decryption](./cj-huks-encryption-decryption-overview.md).  
- [Signing and Signature Verification](./cj-huks-signing-signature-verification-overview.md).  
- [Key Agreement](./cj-huks-key-agreement-overview.md).  
- [Key Derivation](./cj-huks-key-derivation-overview.md).  

## General Development Process  

HUKS operates on data based on key sessions. The following process is used when working with keys:  

1. **(Mandatory)** Initialize a key session [`huks.initSession()`](../../reference/UniversalKeystoreKit/cj-apis-security_huks.md#func-initsessionstring-huksoptions).  

   Pass in the key alias and key operation parameters to initialize a key session and obtain a session handle. The key operation parameters must include the necessary parameters for the corresponding cryptographic algorithm, such as the cryptographic algorithm, key size, key purpose, operation mode, padding mode, hash mode, IV, Nonce, AAD, etc.  

2. **(Optional)** Process data in segments [`huks.updateSession()`](../../reference/UniversalKeystoreKit/cj-apis-security_huks.md#func-updatesessionhukshandleid-huksoptions-bytes).  

   If the data is too large (exceeding 100K) or if certain cryptographic algorithms require it, the data must be processed in segments. Otherwise, this step can be skipped.  

3. **(Mandatory)** Terminate the key session [`huks.finishSession()`](../../reference/UniversalKeystoreKit/cj-apis-security_huks.md#func-finishsessionhukshandleid-huksoptions-bytes).  

   Process the final segment of data and terminate the key session.  

If an error occurs at any stage or if the key operation is no longer needed, the session must be canceled [`huks.abortSession()`](../../reference/UniversalKeystoreKit/cj-apis-security_huks.md#func-abortsessionhukshandleid-huksoptions) to terminate key usage.  

> **Note:**  
>  
> For devices with limited memory, it is recommended that applications split the data according to the device's storage capacity and cyclically call [`huks.initSession()`](../../reference/UniversalKeystoreKit/cj-apis-security_huks.md#func-initsessionstring-huksoptions) and [`huks.finishSession()`](../../reference/UniversalKeystoreKit/cj-apis-security_huks.md#func-finishsessionhukshandleid-huksoptions-bytes) for processing.