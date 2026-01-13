# AES Symmetric Key Encryption and Decryption (GCM Mode)

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

For the corresponding algorithm specifications, please refer to [Symmetric Key Encryption and Decryption Algorithm Specifications: AES](./cj-crypto-sym-encrypt-decrypt-spec.md#aes).

## Encryption

1. Call [createSymKeyGenerator](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createsymkeygeneratorstring) to generate a symmetric key (SymKey) with AES as the key algorithm and 128-bit key length.

   For guidance on generating an AES symmetric key, developers can refer to the example below, combined with [Symmetric Key Generation and Conversion Specifications: AES](./cj-crypto-sym-key-generation-conversion-spec.md#aes) and [Random Symmetric Key Generation](./cj-crypto-generate-sym-key-randomly.md). Note that the reference documents may have parameter differences from the current example, so please pay attention to distinctions when reading.

2. Call [createCipher](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createcipherstring) with the string parameter 'AES128|GCM|PKCS7' to create a Cipher instance with AES128 as the symmetric key type, GCM as the block mode, and PKCS7 as the padding mode, which will be used to perform encryption operations.

3. Call [init](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-initcryptomode-key-paramsspec) to set the mode to encryption (CryptoMode.EncryptMode), specify the encryption key (SymKey), and the encryption parameters for GCM mode (GcmParamsSpec), initializing the encryption Cipher instance.

4. Call [update](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-updatedatablob) to update the data (plaintext).

   There is currently no limit on the length of a single update. Developers can decide how to call update based on the data volume.

   - For small data volumes, you can directly call doFinal after init.
   - For large data volumes, you can call update multiple times, i.e., [Segmented Encryption and Decryption](./cj-crypto-aes-sym-encrypt-decrypt-gcm-by-segment.md).

5. Call [doFinal](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-dofinaldatablob) to obtain the encrypted data.
   Since the data has already been passed via update, pass None for data here.

6. Read [GcmParamsSpec](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#struct-gcmparamsspec).authTag as the authentication information for decryption.
   In GCM mode, the algorithm library currently only supports a 16-byte authTag, which serves as the authentication information during decryption initialization. In the example, the authTag length is exactly 16 bytes.

## Decryption

1. Call [createCipher](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createcipherstring) with the string parameter 'AES128|GCM|PKCS7' to create a Cipher instance with AES128 as the symmetric key type, GCM as the block mode, and PKCS7 as the padding mode, which will be used to perform decryption operations.

2. Call [init](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-initcryptomode-key-paramsspec) to set the mode to decryption (CryptoMode.DecryptMode), specify the decryption key (SymKey), and the decryption parameters for GCM mode (GcmParamsSpec), initializing the decryption Cipher instance.

3. Call [update](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-updatedatablob) to update the data (ciphertext).

4. Call [doFinal](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-dofinaldatablob) to obtain the decrypted data.

## Example

The synchronous method example is as follows:

<!-- compile -->

```cangjie
import kit.CryptoArchitectureKit.*
import ohos.hilog.Hilog

func generateRandom(len: Int32) {
    let rand = createRandom()
    let generateRandSync = rand.generateRandom(len)
    return generateRandSync
}

func genGcmParamsSpec() {
    let ivBlob = generateRandom(12)
    let aadBlob: DataBlob = DataBlob([1, 2, 3, 4, 5, 6, 7, 8]) // 8 bytes
    let arr: Array<UInt8> = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0] // 16 bytes
    let tagBlob: DataBlob = DataBlob() // The GCM authTag is obtained by doFinal() in encryption and passed in params of init() in decryption.
    let gcmParamsSpec: GcmParamsSpec = GcmParamsSpec("GcmParamsSpec", ivBlob, aadBlob, tagBlob)
    return gcmParamsSpec
}

var gcmParams = genGcmParamsSpec()
// Encrypt message.
func encryptMessage(symKey: SymKey, plainText: DataBlob) {
    let cipher = createCipher('AES128|GCM|PKCS7')
    cipher.initialize(CryptoMode.EncryptMode, symKey, gcmParams)
    let encryptUpdate = cipher.update(plainText)
    // In GCM mode encryption, pass None to doFinal to obtain tag data and update it in the gcmParams object.
    gcmParams.authTag = cipher.doFinal(Option<DataBlob>.None)
    return encryptUpdate
}

// Decrypt message.
func decryptMessage(symKey: SymKey, cipherText: DataBlob) {
    let decoder = createCipher('AES128|GCM|PKCS7')
    decoder.initialize(CryptoMode.DecryptMode, symKey, gcmParams)
    let decryptUpdate = decoder.update(cipherText)
    decoder.doFinal(Option<DataBlob>.None)
    return decryptUpdate
}

func genSymKeyByData(symKeyData: Array<UInt8>) {
    let symKeyBlob: DataBlob = DataBlob(symKeyData)
    let aesGenerator = createSymKeyGenerator('AES128')
    let symKey = aesGenerator.convertKey(symKeyBlob)
    Hilog.info(0,"",'convertKey success')
    return symKey
}

func test() {
    let keyData: Array<UInt8> = [83, 217, 231, 76, 28, 113, 23, 219, 250, 71, 209, 210, 205, 97, 32, 159]
    let symKey = genSymKeyByData(keyData)
    let message = "This is a test"
    let plainText: DataBlob = DataBlob(message.toArray())
    let encryptText = encryptMessage(symKey, plainText)
    let decryptText = decryptMessage(symKey, encryptText)
    if (plainText.data.toString() == decryptText.data.toString()) {
        Hilog.info(0,"",'decrypt ok')
        Hilog.info(0,"",'decrypt plainText: ' + String.fromUtf8(decryptText.data))
    } else {
        Hilog.error(0,"",'decrypt failed')
    }
}
```