# Random Symmetric Key Generation  

Taking AES and SM4 as examples, randomly generate a symmetric key (SymKey) and obtain its binary data.  

The symmetric key can be used for subsequent encryption and decryption operations, while the binary data can be stored or transmitted.  

## Random AES Key Generation  

For the corresponding algorithm specifications, refer to [Symmetric Key Generation and Conversion Specifications: AES](./cj-crypto-sym-key-generation-conversion-spec.md#aes).  

1. Call [createSymKeyGenerator](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createsymkeygeneratorstring), specify the string parameter 'AES256', and create a symmetric key generator (SymKeyGenerator) with AES as the key algorithm and a key length of 256 bits.  

2. Call [generateSymKey](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-generatesymkey) to randomly generate a symmetric key (SymKey).  

3. Call [getEncoded](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-getencoded) to obtain the binary data of the key.  

## Example: Random AES Key Generation  

<!-- compile -->  

```cangjie  
import kit.CryptoArchitectureKit.*  
import ohos.hilog.Hilog  

func testSyncGenerateAesKey() {  
    // Create a SymKeyGenerator instance.  
    let symKeyGenerator = createSymKeyGenerator('AES256')  
    // Use the key generator to randomly generate a symmetric key.  
    let promiseSymKey = symKeyGenerator.generateSymKey()  
    // Obtain the binary data of the symmetric key, outputting a 256-bit key. The length is 32 bytes.  
    let encodedKey = promiseSymKey.getEncoded()  
    Hilog.info(0,"",'key hex: ${encodedKey.data}')  
}  
 ```  

## Random SM4 Key Generation  

For the corresponding algorithm specifications, refer to [Symmetric Key Generation and Conversion Specifications: SM4](./cj-crypto-sym-key-generation-conversion-spec.md#sm4).  

1. Call [createSymKeyGenerator](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createsymkeygeneratorstring), specify the string parameter 'SM4_128', and create a symmetric key generator (SymKeyGenerator) with SM4 as the key algorithm and a key length of 128 bits.  
   If developers need to use other algorithms, please modify the string parameter here accordingly.  

2. Call [generateSymKey](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-generatesymkey) to randomly generate a symmetric key (SymKey).  

3. Call [getEncoded](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-getencoded) to obtain the binary data of the key.  

## Example: Random SM4 Key Generation  

<!-- compile -->  

```cangjie  
import kit.CryptoArchitectureKit.*  
import ohos.hilog.Hilog  

func testSyncGenerateSm4Key() {  
    // Create a SymKeyGenerator instance.  
    let symKeyGenerator = createSymKeyGenerator('SM4_128')  
    // Use the key generator to randomly generate a symmetric key.  
    let promiseSymKey = symKeyGenerator.generateSymKey()  
    // Obtain the binary data of the symmetric key, outputting a 128-bit key. The length is 16 bytes.  
    let encodedKey = promiseSymKey.getEncoded()  
    Hilog.info(0,"",'key hex: ${encodedKey.data}')  
}  
```