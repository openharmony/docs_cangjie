# Using AES Symmetric Key (CCM Mode) for Encryption and Decryption

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

For the corresponding algorithm specifications, please refer to [Symmetric Key Encryption and Decryption Algorithm Specifications: AES](./cj-crypto-sym-encrypt-decrypt-spec.md#aes).

## Encryption

1. Call [createSymKeyGenerator](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createsymkeygeneratorstring) and [generateSymKey](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-generatesymkey) to generate a symmetric key (SymKey) with AES as the key algorithm and a key length of 128 bits.

   For guidance on generating an AES symmetric key, developers can refer to the example below, along with [Symmetric Key Generation and Conversion Specifications: AES](./cj-crypto-sym-key-generation-conversion-spec.md#aes) and [Random Symmetric Key Generation](./cj-crypto-generate-sym-key-randomly.md). Note that the reference documents may have parameter differences from the current example, so please pay attention to distinctions while reading.

2. Call [createCipher](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createcipherstring) with the string parameter 'AES128|CCM' to create a Cipher instance for encryption operations, specifying AES128 as the symmetric key type and CCM as the block mode.

3. Call [init](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-initcryptomode-key-paramsspec) to set the mode to encryption (CryptoMode.EncryptMode), specify the encryption key (SymKey), and initialize the encryption Cipher instance with the corresponding encryption parameters for CCM mode (CcmParamsSpec).

4. Call [update](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-updatedatablob) to update the data (plaintext).

   There is currently no limit on the length of a single update operation. Developers can determine how to call update based on the data volume.

   > **Note:**
   > CCM mode does not support segmented encryption and decryption.

5. Call [doFinal](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-dofinaldatablob) to obtain the encrypted data.
   Since the data has already been passed via update, pass None for the data parameter here.

6. Read [CcmParamsSpec.authTag](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#struct-ccmparamsspec) as the authentication information for decryption.

   In CCM mode, the algorithm library currently only supports a 12-byte authTag, which serves as the authentication information for initialization during decryption. In the example, the authTag happens to be 12 bytes.

## Decryption

1. Call [createCipher](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createcipherstring) with the string parameter 'AES128|CCM' to create a Cipher instance for decryption operations, specifying AES128 as the symmetric key type and CCM as the block mode.

2. Call [init](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-initcryptomode-key-paramsspec) to set the mode to decryption (CryptoMode.DecryptMode), specify the decryption key (SymKey), and initialize the decryption Cipher instance with the corresponding decryption parameters for CCM mode (CcmParamsSpec).

3. Call [doFinal](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-dofinaldatablob) to obtain the decrypted data.

## Example

The synchronous method example is as follows:

<!-- compile -->

```cangjie
import kit.CryptoArchitectureKit.*
import ohos.hilog.Hilog

func genCcmParamsSpec() {
    let rand: Random = createRandom()
    let ivBlob: DataBlob = rand.generateRandom(7)
    let aadBlob: DataBlob = rand.generateRandom(8)
    let dataTag: Array<UInt8> = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0] // 12 bytes
    let tagBlob: DataBlob = DataBlob(dataTag)
    // In CCM mode, authTag is obtained from the doFinal result during encryption and passed to the params parameter of the init function during decryption.
    let ccmParamsSpec: CcmParamsSpec = CcmParamsSpec("CcmParamsSpec", ivBlob, aadBlob, tagBlob)
    return ccmParamsSpec
}

var ccmParams = genCcmParamsSpec()
// Encrypt message.
func encryptMessage(symKey: SymKey, plainText: DataBlob) {
    let cipher = createCipher('AES128|CCM')
    cipher.initialize(CryptoMode.EncryptMode, symKey, ccmParams)
    let encryptUpdate = cipher.update(plainText);
    // In CCM mode encryption, pass None to doFinal to obtain the tag data and update it in the ccmParams object.
    ccmParams.authTag = cipher.doFinal(Option<DataBlob>.None);
    return encryptUpdate
}

// Decrypt message.
func decryptMessage(symKey: SymKey, cipherText: DataBlob) {
    let decoder = createCipher('AES128|CCM')
    decoder.initialize(CryptoMode.DecryptMode, symKey, ccmParams)
    let decryptData = decoder.doFinal(cipherText)
    return decryptData
}

func genSymKeyByData(symKeyData: Array<UInt8>) {
    let symKeyBlob: DataBlob = DataBlob(symKeyData)
    let aesGenerator = createSymKeyGenerator('AES128')
    let symKey = aesGenerator.convertKey(symKeyBlob)
    Hilog.info(0,"",'convertKey success')
    return symKey
}
```