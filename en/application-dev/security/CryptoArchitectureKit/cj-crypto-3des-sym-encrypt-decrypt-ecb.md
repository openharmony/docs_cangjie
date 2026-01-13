# Using 3DES Symmetric Key (ECB Mode) for Encryption and Decryption

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

For corresponding algorithm specifications, please refer to [Symmetric Key Encryption/Decryption Algorithm Specifications: 3DES](./cj-crypto-sym-encrypt-decrypt-spec.md#3des).

## Encryption

1. Call [createSymKeyGenerator](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createsymkeygeneratorstring) and [convertKey](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-convertkeydatablob) to generate a symmetric key (SymKey) with the 3DES algorithm and a key length of 192 bits.

   For guidance on generating a 3DES symmetric key, developers can refer to the example below, along with [Symmetric Key Generation and Conversion Specifications: 3DES](./cj-crypto-sym-key-generation-conversion-spec.md#3des) and [Converting Binary Data to Symmetric Key](./cj-crypto-convert-binary-data-to-sym-key.md). Note that the reference documents may have parameter differences from the current example, so please pay attention to distinctions when reading.

2. Call [createCipher](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createcipherstring) with the string parameter '3DES192|ECB|PKCS7' to create a Cipher instance for encryption operations, specifying 3DES192 as the symmetric key type, ECB as the block mode, and PKCS7 as the padding mode.

3. Call [init](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-initcryptomode-key-paramsspec) to set the mode to encryption (CryptoMode.EncryptMode), specify the encryption key (SymKey), and initialize the encryption Cipher instance.

   ECB mode does not require encryption parameters, so directly pass None.

4. Call [update](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-updatedatablob) to update data (plaintext).

   - For small data volumes, you can directly call doFinal after initialization.
   - For large data volumes, you can call update multiple times, i.e., perform segmented encryption/decryption.
   - The threshold for data volume size can be determined by the user. For example, use update for data larger than 20 bytes.

5. Call [doFinal](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-dofinaldatablob) to obtain the encrypted data.

   Since the data has already been passed via update, pass None here for data.

## Decryption

1. Call [createCipher](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createcipherstring) with the string parameter '3DES192|ECB|PKCS7' to create a Cipher instance for decryption operations, specifying 3DES192 as the symmetric key type, ECB as the block mode, and PKCS7 as the padding mode.

2. Call [init](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-initcryptomode-key-paramsspec) to set the mode to decryption (CryptoMode.DecryptMode), specify the decryption key (SymKey), and initialize the decryption Cipher instance. ECB mode does not require encryption parameters, so directly pass None.

3. Call [update](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-updatedatablob) to update data (ciphertext).

4. Call [doFinal](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-dofinaldatablob) to obtain the decrypted data.

## Example

The synchronous method example is as follows:

<!-- compile -->

```cangjie
import kit.CryptoArchitectureKit.*
import ohos.hilog.Hilog

// Encrypt message.
func encryptMessage(symKey: SymKey, plainText: DataBlob) {
    let cipher = createCipher('3DES192|ECB|PKCS7')
    cipher.initialize(CryptoMode.EncryptMode, symKey, Option<ParamsSpec>.None)
    let encryptData = cipher.doFinal(plainText)
    return encryptData
}

// Decrypt message.
func decryptMessage(symKey: SymKey, cipherText: DataBlob) {
    let decoder = createCipher('3DES192|ECB|PKCS7')
    decoder.initialize(CryptoMode.DecryptMode, symKey, Option<ParamsSpec>.None)
    let decryptData = decoder.doFinal(cipherText)
    return decryptData
}

func genSymKeyByData(symKeyData: Array<UInt8>) {
    let symKeyBlob: DataBlob = DataBlob(symKeyData)
    let symGenerator = createSymKeyGenerator('3DES192')
    let symKey = symGenerator.convertKey(symKeyBlob)
    Hilog.info(0,"",'convertKey success')
    return symKey
}

func test() {
    let keyData: Array<UInt8> = [238, 249, 61, 55, 128, 220, 183, 224, 139, 253, 248, 239, 239, 41, 71, 25, 235, 206,
        230, 162, 249, 27, 234, 114]
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