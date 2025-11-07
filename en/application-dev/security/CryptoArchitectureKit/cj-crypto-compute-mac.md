# Message Authentication Code Calculation

MAC (Message Authentication Code) enables integrity verification of messages by using a shared secret key between communicating parties to detect tampering or forgery attempts.

HMAC (Hash-based Message Authentication Code) is a hash-based message authentication code algorithm.

HMAC generates a message authentication code by taking both the shared secret key and the message as inputs through a specified digest algorithm, which is used to verify the integrity of transmitted messages. HMAC enhances the message digest algorithm by incorporating a secret key input, ensuring message authenticity. The generated message authentication code has a fixed length.

## Supported Algorithms and Specifications

When creating an HMAC message authentication code, you must use the algorithms listed in the "Supported Types" column of the table below to specify the HMAC message authentication code specifications.

| Digest Algorithm | Supported Types | API Version |
| ---------------- | --------------- | ----------- |
| HASH | SHA1 | 12+ |
| HASH | SHA224 | 12+ |
| HASH | SHA256 | 12+ |
| HASH | SHA384 | 12+ |
| HASH | SHA512 | 12+ |
| HASH | SM3 | 12+ |
| HASH | MD5 | 12+ |

## Development Procedure

When passing data through the `update` interface, you can either [pass all data at once](#hmac-one-time-input) or manually segment the data and [update it in segments](#segmented-hmac). For the same data, whether segmented or not, the calculation results remain identical. For large volumes of data, developers can choose whether to segment the input based on actual requirements.

Below are example codes for both approaches.

### HMAC (One-Time Input)

1. Call [createMac](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createmacstring), specifying the SHA256 digest algorithm, to generate a message authentication code instance (Mac).

2. Call [createSymKeyGenerator](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createsymkeygeneratorstring) and [convertKey](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-convertkeydatablob) to generate a symmetric key (SymKey) with the HMAC key algorithm.
   For detailed guidance on generating symmetric keys, refer to [Generating Symmetric Keys from Binary Data](./cj-crypto-convert-binary-data-to-sym-key.md).

3. Call [init](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-initsymkey), specifying the shared symmetric key (SymKey), to initialize the Mac object.

4. Call [update](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-updatedatablob-1), passing the custom message to calculate the message authentication code. There is no length limit for a single `update` call.

5. Call [doFinal](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-dofinal) to obtain the Mac calculation result.

6. Call [getMacLength](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-getmaclength) to get the length of the Mac message authentication code in bytes.

### Example: One-Time Input for Message Authentication Code Calculation

<!-- compile -->

```cangjie
import kit.CryptoArchitectureKit.*
import ohos.hilog.Hilog

func genSymKeyByData(symKeyData: Array<UInt8>) {
    let symKeyBlob: DataBlob = DataBlob(symKeyData)
    let aesGenerator = createSymKeyGenerator('HMAC')
    let symKey = aesGenerator.convertKey(symKeyBlob)
    Hilog.info(0,"",'convertKey success')
    return symKey
}

func doHmacBySync() {
    // Decode the string into Uint8Array using UTF-8, with a fixed 128-bit key (16 bytes)
    let keyData = Array<UInt8>(16, repeat:0)
    let key = genSymKeyByData(keyData)
    let macAlgName = 'SHA256' // Digest algorithm name
    let message = 'hmacTestMessgae' // Data for HMAC calculation
    let mac = createMac(macAlgName)
    mac.initialize(key)
    // For small data volumes, perform a single update with all data (no input length restriction)
    mac.update(DataBlob(keyData))
    let macResult = mac.doFinal()
    Hilog.info(0,"",'[Sync]HMAC result: ${macResult.data}')
    let macLen = mac.getMacLength()
    Hilog.info(0,"",'HMAC len: ${macLen}')
}
```

### Segmented HMAC

1. Call [createMac](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createmacstring), specifying the SHA256 digest algorithm, to generate a message authentication code instance (Mac).

2. Call [createSymKeyGenerator](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createsymkeygeneratorstring) to generate a symmetric key (SymKey) with the HMAC key algorithm.
   For detailed guidance on generating symmetric keys, refer to [Generating Symmetric Keys from Binary Data](./cj-crypto-convert-binary-data-to-sym-key.md).

3. Call [init](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-initsymkey), specifying the shared symmetric key (SymKey), to initialize the Mac object.

4. Pass the custom message, setting the data input per segment to 20 bytes, and call [update](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-updatedatablob-1) multiple times to calculate the message authentication code.

5. Call [doFinal](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-dofinal) to obtain the Mac calculation result.

6. Call [getMacLength](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-getmaclength) to get the length of the Mac message authentication code in bytes.

### Example: Segmented Input for Message Authentication Code Calculation

<!-- compile -->

```cangjie
import kit.CryptoArchitectureKit.*
import ohos.hilog.Hilog

func genSymKeyByData(symKeyData: Array<UInt8>) {
    let symKeyBlob: DataBlob = DataBlob(symKeyData)
    let aesGenerator = createSymKeyGenerator('HMAC')
    let symKey = aesGenerator.convertKey(symKeyBlob)
    Hilog.info(0,"",'convertKey success')
    return symKey
}

func doHmacBySync() {
    // Decode the string into Uint8Array using UTF-8, with a fixed 128-bit key (16 bytes)
    let keyData = Array<UInt8>(16, repeat:0)
    let key = genSymKeyByData(keyData)
    let macAlgName = 'SHA256' // Digest algorithm name
    let message = 'aaaaa.....bbbbb.....ccccc.....ddddd.....eee'.toArray() // Data for HMAC calculation
    let mac = createMac(macAlgName)
    mac.initialize(key)
    let updateLength = 20; // Assume segmentation in 20-byte units (no actual requirement)
    let size = message.size
    // For small data volumes, perform a single update with all data (no input length restriction)
    for (i in 0..size : updateLength) {
        let len = if (i + updateLength > size) {
            size
        } else {
            i + updateLength
        }
        let updateMessage = message[i..len]
        let updateMessageBlob: DataBlob = DataBlob(updateMessage)
        mac.update(updateMessageBlob)
    }
    let macResult = mac.doFinal()
    Hilog.info(0,"",'[Sync]HMAC result: ${macResult.data}')
    let macLen = mac.getMacLength()
    Hilog.info(0,"",'HMAC len: ${macLen}')
}
```