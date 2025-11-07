# Generating Keys from Specified Binary Data

Taking 3DES and HMAC as examples, this section describes how to generate a symmetric key (SymKey) from specified binary data. This involves converting external or stored binary data into a key object that can be used for subsequent cryptographic operations like encryption and decryption.

## Generating a 3DES Key from Specified Binary Data

For the corresponding algorithm specifications, refer to [Symmetric Key Generation Specifications: 3DES](./cj-crypto-sym-key-generation-conversion-spec.md#3des).

1. Obtain the 3DES binary key data and encapsulate it into a [DataBlob](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#struct-datablob) object.

2. Call [createSymKeyGenerator](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createsymkeygeneratorstring) with the string parameter '3DES192' to create a symmetric key generator (SymKeyGenerator) for the 3DES algorithm with a key length of 192 bits.

3. Call [convertKey](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-convertkeydatablob) to generate a symmetric key (SymKey) from the specified binary data.

4. Call [getEncoded](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-getencoded) to retrieve the binary data of the generated key.

Example of generating a 3DES key:

<!-- compile -->

```cangjie
import kit.CryptoArchitectureKit.*
import ohos.hilog.Hilog

func genKeyMaterialBlob(): DataBlob {
    let arr: Array<UInt8> = [0xba, 0x3d, 0xc2, 0x71, 0x21, 0x1e, 0x30, 0x56, 0xad, 0x47, 0xfc, 0x5a, 0x46, 0x39, 0xee,
        0x7c, 0xba, 0x3b, 0xc2, 0x71, 0xab, 0xa0, 0x30, 0x72] // Key length is 192 bits (24 bytes).
    return DataBlob(arr)
}

func testConvertSymKey() {
    // Create a SymKeyGenerator instance.
    let symKeyGenerator = createSymKeyGenerator('3DES192')
    // Generate a symmetric key from the specified data.
    let keyMaterialBlob = genKeyMaterialBlob()
    let key = symKeyGenerator.convertKey(keyMaterialBlob)
    let encodedKey = key.getEncoded() // Retrieve the binary data of the symmetric key as a byte array. Length is 24 bytes.
    Hilog.info(0,"",'key getEncoded hex ${encodedKey.data}')
}
```

## Generating an HMAC Key from Specified Binary Data

For the corresponding algorithm specifications, refer to [Symmetric Key Generation and Conversion Specifications: HMAC](./cj-crypto-sym-key-generation-conversion-spec.md#hmac).

1. Obtain the HMAC binary key data and encapsulate it into a DataBlob object.

2. Call [createSymKeyGenerator](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createsymkeygeneratorstring) with the string parameter 'HMAC' to create a symmetric key generator (SymKeyGenerator) for the HMAC algorithm with a key length ranging from [1, 32768] bits.

3. Call [convertKey](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-convertkeydatablob) to generate a symmetric key (SymKey) from the specified binary data.

4. Call [getEncoded](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-getencoded) to retrieve the binary data of the generated key.

Example of generating an HMAC key:

<!-- compile -->

```cangjie
import kit.CryptoArchitectureKit.*
import ohos.hilog.Hilog

func testConvertKey() {
    // Symmetric key length is 64 bytes (512 bits).
    let keyMessage = '12345678abcdefgh12345678abcdefgh12345678abcdefgh12345678abcdefgh'
    let keyBlob: DataBlob = DataBlob(keyMessage.toArray())
    let symKeyGenerator = createSymKeyGenerator('HMAC')
    let key = symKeyGenerator.convertKey(keyBlob)
    let encodedKey = key.getEncoded()
    Hilog.info(0,"",'key encoded data：${encodedKey.data}')
}
```