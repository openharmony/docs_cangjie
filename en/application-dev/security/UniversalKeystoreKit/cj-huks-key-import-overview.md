# Key Import Introduction and Algorithm Specifications  

If a service generates keys outside of HUKS (e.g., through inter-application negotiation or server-side generation), the service can import these keys into HUKS for management. Once a key is imported into HUKS, its plaintext is only accessible within a secure environment during its lifecycle and will never be transmitted outside the secure environment, ensuring that no one can obtain the plaintext of the key.  

Key import methods include [Plaintext Import](#plaintext-import) and [Encrypted Import](#encrypted-import).  

## Plaintext Import  

This method directly imports the key plaintext into HUKS. During the import process, the key plaintext is exposed in a non-secure environment, making it generally suitable for lightweight devices or low-security services.  

- **Recommended key types for this method**: Public keys of asymmetric keys.  
- **Not recommended key types for this method**: Symmetric keys, asymmetric key pairs.  

> **Note:**  
>  
> Lightweight devices only support plaintext import and do not support encrypted import.  

## Encrypted Import  

This method allows the service to establish an end-to-end encrypted transmission channel with HUKS, securely importing the key into HUKS and ensuring the key is not leaked during the import process. It is suitable for high-security-sensitive services. Compared to plaintext import, encrypted import involves more steps and more complex key materials.  

**Recommended key types for this method**: Symmetric keys, asymmetric key pairs.  

The following figure shows the development sequence diagram for encrypted key import.  

![Encrypted Key Import Development Sequence Diagram](./figures/加密导入密钥开发顺序图.png)  

According to the development process, the following HUKS capabilities need to be invoked sequentially during encrypted key import:  

- Generate an asymmetric key pair and export the public key for inter-device key agreement.  
- Generate a symmetric key to encrypt the key to be imported.  
- Use the symmetric key to encrypt the key to be imported, forming the key ciphertext.  
- Import the encrypted key.  
- Delete the key.  

The [public key plaintext material returned by the export key interface is encapsulated in **X.509** format](./cj-huks-concepts.md#公钥材料格式). The key material in the encrypted key import interface must adhere to the **Length<sub>Data</sub>-Data** encapsulation format, such as: [(Length<sub>part1</sub>Data<sub>part1</sub>)……(Length<sub>partn</sub>Data<sub>partn</sub>)].  

> **Note:**  
>  
> For encrypted key import, the agreement algorithms supported are ECDH and X25519. The Shared_Key derived from the agreement is used to encrypt Caller_Kek using the AES-GCM algorithm. For the corresponding algorithm suite definitions, see [HuksUnwrapSuite](../../reference/UniversalKeystoreKit/cj-apis-security_huks.md#class-huksunwrapsuite).  

### Encrypted Key Import Material Format  

| Content | Length |  
| :-------- | :-------- |  
| Service public key length L<sub>Caller_Pk</sub> | 4 bytes |  
| Service public key Caller_Pk | L<sub>Caller_Pk</sub> bytes |  
| Shared_Key encryption parameter AAD2 length L<sub>AAD2</sub> | 4 bytes |  
| Shared_Key encryption parameter AAD2 | L<sub>AAD2</sub> bytes |  
| Shared_Key encryption parameter Nonce2 length L<sub>Nonce2</sub> | 4 bytes |  
| Shared_Key encryption parameter Nonce2 | L<sub>Nonce2</sub> bytes |  
| Shared_Key encryption parameter TAG2 length L<sub>TAG2</sub> | 4 bytes |  
| Shared_Key encryption parameter TAG2 | L<sub>TAG2</sub> bytes |  
| Caller_Kek ciphertext length L<sub>Caller_Kek_enc</sub> | 4 bytes |  
| Caller_Kek ciphertext Caller_Kek_enc | L<sub>Caller_Kek_enc</sub> bytes |  
| Caller_Kek encryption parameter AAD3 length L<sub>AAD3</sub> | 4 bytes |  
| Caller_Kek encryption parameter AAD3 | L<sub>AAD3</sub> bytes |  
| Caller_Kek encryption parameter Nonce3 length L<sub>Nonce3</sub> | 4 bytes |  
| Caller_Kek encryption parameter Nonce3 | L<sub>Nonce3</sub> bytes |  
| Caller_Kek encryption parameter TAG3 length L<sub>TAG3</sub> | 4 bytes |  
| Caller_Kek encryption parameter TAG3 | L<sub>TAG3</sub> bytes |  
| Key plaintext material length size L<sub>To_Import_Key_size</sub> | 4 bytes |  
| Key plaintext material length To_Import_Key_size | L<sub>To_Import_Key_size</sub> bytes |  
| To_Import_Key ciphertext length L<sub>To_Import_Key_enc</sub> | 4 bytes |  
| To_Import_Key ciphertext To_Import_Key_enc | L<sub>To_Import_Key_enc</sub> bytes |  

## Supported Algorithms  

The following are the specifications supported for key import.  

<!--Del-->  
For OpenHarmony, vendor adaptation of key management services is divided into mandatory and optional specifications. Mandatory specifications are algorithm specifications supported by all vendors. For optional specifications, vendors decide whether to implement them based on actual circumstances. If needed, refer to the specific vendor's documentation to ensure support before use.  

**Developers are advised to use mandatory specifications to ensure full platform compatibility.**  
<!--DelEnd-->  

> **Note:**  
>  
> When importing RSA keys, the public key must be greater than or equal to 65537.  

### Standard Device Specifications  

| Algorithm | Supported Key Lengths | API Level | <!--DelCol4-->Mandatory Specification |  
| :-------- | :-------- | :-------- | :-------- |  
| AES | 128, 192, 256 | 15+ | Yes |  
| <!--DelRow-->RSA | 512, 768, 1024 | 15+ | No |  
| RSA | 2048, 3072, 4096 | 15+ | Yes |  
| RSA | 1024-2048 (inclusive), must be multiples of 8 | 15+ | Yes |  
| HMAC | 8-1024 (inclusive), must be multiples of 8 | 15+ | Yes |  
| <!--DelRow-->ECC | 224 | 15+ | No |  
| ECC | 256, 384, 521 | 15+ | Yes |  
| ED25519 | 256 | 15+ | Yes |  
| X25519 | 256 | 15+ | Yes |  
| <!--DelRow-->DSA | 512-1024 (inclusive), multiples of 8 | 15+ | No |  
| DH | 2048 | 15+ | Yes |  
| <!--DelRow-->DH | 3072, 4096 | 15+ | No |  
| SM2 | 256 | 15+ | Yes |  
| SM4 | 128 | 15+ | Yes |  
| DES | 64 | 15+ | Yes |  
| 3DES | 128, 192 | 15+ | Yes |  

### Lightweight Device Specifications  

<!--Del-->  
For lightweight devices, OEM vendors decide whether to implement the listed specifications based on actual circumstances. If needed, refer to the specific vendor's documentation to ensure support before use.  
<!--DelEnd-->  

| Algorithm | Supported Key Lengths | API Level |  
| :-------- | :-------- | :-------- |  
| AES | 128, 192, 256 | 15+ |  
| DES | 64 | 15+ |  
| 3DES | 128, 192 | 15+ |  
| RSA | 1024-2048 (inclusive), must be multiples of 8 | 15+ |  
| HMAC | 8-1024 (inclusive), must be multiples of 8 | 15+ |  
| CMAC | 128 | 15+ |  

## Key Import Formats  

HUKS supports a wide range of key types for import, and the corresponding key material formats vary. The table below summarizes the key types supported by HUKS for import and their corresponding key material formats.  

| Key Type | Algorithm | Import Format |  
| :-------- | :-------- | :-------- |  
| Symmetric Key | - | Key byte data |  
| Asymmetric Key - Key Pair | - | [Key Pair Material Format](./cj-huks-concepts.md#密钥对材料格式) |  
| Asymmetric Key - Public Key | ED25519, X25519 | Refer to [X25519 Public Key Import](./cj-huks-import-key-in-plaintext.md#导入X25519密钥公钥) |  
| Asymmetric Key - Public Key | RSA, ECC, ECDH, DSA, DH, SM2 | DER format compliant with X.509 specification |