# Segment Encryption and Decryption Using SM4 Symmetric Key (GCM Mode)

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

For corresponding algorithm specifications, refer to [Symmetric Key Encryption/Decryption Algorithm Specifications: SM4](./cj-crypto-sym-encrypt-decrypt-spec.md#sm4).

## Encryption

1. Call [createSymKeyGenerator](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createsymkeygeneratorstring) to generate a symmetric key (SymKey) with SM4 algorithm and 128-bit key length.

    For guidance on generating SM4 symmetric keys, developers can refer to the example below, along with [Symmetric Key Generation and Conversion Specifications: SM4](./cj-crypto-sym-key-generation-conversion-spec.md#sm4) and [Random Symmetric Key Generation](./cj-crypto-generate-sym-key-randomly.md). Note that reference documents may have parameter differences from this example—please distinguish carefully when reading.

2. Call [createCipher](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createcipherstring) with the string parameter 'SM4_128|GCM|PKCS7' to create a Cipher instance configured for SM4_128 symmetric key, GCM block mode, and PKCS7 padding mode, which will perform encryption operations.

3. Call [init](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-initcryptomode-key-paramsspec) to set the mode to encryption (CryptoMode.EncryptMode), specify the encryption key (SymKey), and provide GCM mode parameters (GcmParamsSpec) to initialize the Cipher instance.

4. Set the data chunk size to 20 bytes and call [update](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-updatedatablob) multiple times to process data (plaintext).

    - There is no restriction on the single `update` length; developers can determine how to call `update` based on data volume.
    - It is recommended to check if each `update` result is an empty array and concatenate non-empty results to form the complete ciphertext. Different specifications may affect `update` behavior:
        - For ECB and CBC modes, encryption operates in blocks. If an `update` fills a block, it outputs ciphertext; otherwise, it returns an empty array and retains unencrypted data for the next `update`. During `doFinal`, remaining data is padded and encrypted.
        - For stream cipher modes (e.g., CTR and OFB), ciphertext length typically matches plaintext length.

5. Call [doFinal](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-dofinaldatablob) to obtain the final encrypted data.

    Since data was already passed via `update`, pass `None` for the `data` parameter here.

6. Retrieve [GcmParamsSpec](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#struct-gcmparamsspec).authTag as authentication data for decryption.

    In GCM mode, the last 16 bytes of encrypted data must be extracted as authentication information for decryption initialization. In this example, `authTag` is exactly 16 bytes.

## Decryption

1. Call [createCipher](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createcipherstring) with the string parameter 'SM4_128|GCM|PKCS7' to create a Cipher instance configured for SM4_128 symmetric key, GCM block mode, and PKCS7 padding mode, which will perform decryption operations.

2. Call [init](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-initcryptomode-key-paramsspec) to set the mode to decryption (CryptoMode.DecryptMode), specify the decryption key (SymKey), and provide GCM mode parameters (GcmParamsSpec) to initialize the Cipher instance.

3. Set the data chunk size to 20 bytes and call [update](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-updatedatablob) multiple times to process data (ciphertext).

4. Call [doFinal](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-dofinaldatablob) to obtain the final decrypted data.

## Example

Synchronous method example:

<!-- compile -->

```cangjie
import kit.CryptoArchitectureKit.*
import std.collection.ArrayList
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
    let cipher = createCipher('SM4_128|GCM|PKCS7')
    cipher.initialize(CryptoMode.EncryptMode, symKey, gcmParams)
    let updateLength = 20 // Assume 20-byte chunks for segmented update (no actual requirement).
    let cipherText = ArrayList<UInt8>()
    let size = plainText.data.size
    for (i in 0..size : updateLength) {
        let len = if (i + updateLength > size) {
            size
        } else {
            i + updateLength
        }
        let updateMessage = plainText.data[i..len]
        let updateMessageBlob: DataBlob = DataBlob(updateMessage)
        // Segmented update.
        let updateOutput = cipher.update(updateMessageBlob)
        // Concatenate update results to form ciphertext (for some modes, doFinal results may also need concatenation.
        // In GCM mode, doFinal only provides authTag, so no concatenation is needed here).
        cipherText.add(all: updateOutput.data)
    }
    gcmParams.authTag = cipher.doFinal(Option<DataBlob>.None)
    let cipherBlob: DataBlob = DataBlob(cipherText.toArray())
    return cipherBlob
}

// Decrypt message.
func decryptMessage(symKey: SymKey, cipherText: DataBlob) {
    let decoder = createCipher('SM4_128|GCM|PKCS7')
    decoder.initialize(CryptoMode.DecryptMode, symKey, gcmParams)
    let updateLength = 20 // Assume 20-byte chunks for segmented update (no actual requirement).
    let decryptText = ArrayList<UInt8>()
    let size = cipherText.data.size
    for (i in 0..size : updateLength) {
        let len = if (i + updateLength > size) {
            size
        } else {
            i + updateLength
        }
        let updateMessage = cipherText.data[i..len]
        let updateMessageBlob: DataBlob = DataBlob(updateMessage)
        // Segmented update.
        let updateOutput = decoder.update(updateMessageBlob)
        // Concatenate update results to form plaintext.
        decryptText.add(all: updateOutput.data)
    }
    decoder.doFinal(Option<DataBlob>.None)
    let decryptBlob: DataBlob = DataBlob(decryptText.toArray());
    return decryptBlob;
}

func genSymKeyByData(symKeyData: Array<UInt8>) {
    let symKeyBlob: DataBlob = DataBlob(symKeyData)
    let aesGenerator = createSymKeyGenerator('SM4_128')
    let symKey = aesGenerator.convertKey(symKeyBlob)
    Hilog.info(0,"",'convertKey success')
    return symKey
}

func test() {
    let keyData: Array<UInt8> = [83, 217, 231, 76, 28, 113, 23, 219, 250, 71, 209, 210, 205, 97, 32, 159]
    let symKey = genSymKeyByData(keyData)
    let message = "aaaaa.....bbbbb.....ccccc.....ddddd.....eee" // Assume 43-byte message (UTF-8 encoded length remains 43 bytes).
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