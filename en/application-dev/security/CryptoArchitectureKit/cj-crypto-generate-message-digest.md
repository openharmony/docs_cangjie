# SHA256 Message Digest Calculation

For the corresponding algorithm specifications, please refer to [Message Digest Calculation Algorithm Specifications](./cj-crypto-generate-message-digest-overview.md#supported-algorithms-and-specifications).

> **Note:**
>
> Starting from API version 12, lightweight smart wearable devices support message digest calculation and operations.

## Development Steps

When passing data through the update interface, you can either [pass all data at once](#digest-algorithm-single-pass) or manually segment the data and then [perform segmented updates](#segmented-digest-algorithm). For the same segment of data, the calculation results will be identical. For large volumes of data, developers can choose whether to pass the data in segments based on actual requirements.

Example codes for both approaches are provided below.

### Digest Algorithm (Single Pass)

1. Call [createMd](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createmdstring), specify the digest algorithm as SHA256, and generate a digest instance (Md).

2. Call [update](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-updatedatablob-2), pass in custom message data, and perform digest update calculations. There is no length restriction for a single update operation.

3. Call [digest](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-digest) to obtain the digest calculation result.

4. Call [getMdLength](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-getmdlength) to get the digest calculation length in bytes.

### Example: Single Pass Data Input to Obtain Digest Result

<!-- compile -->

```cangjie
import kit.CryptoArchitectureKit.*
import ohos.hilog.Hilog

func doMd() {
    let mdAlgName = 'SHA256' // Digest algorithm name.
    let message = 'mdTestMessage' // Data to be digested.
    let md = createMd(mdAlgName)
    // For small data volumes, perform a single update by passing all data at once. No input length restrictions apply.
    md.update(DataBlob(message.toArray()))
    let mdResult = md.digest()
    Hilog.info(0,"",'[Sync]:Md result: ${mdResult.data}')
    let mdLen = md.getMdLength()
    Hilog.info(0,"","md len: ${mdLen}")
}
```

### Segmented Digest Algorithm

1. Call [createMd](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-createmdstring), specify the digest algorithm as SHA256, and generate a digest instance (Md).

2. Pass in custom message data, set the single-pass data volume to 20 bytes, and call [update](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-updatedatablob-2) multiple times to perform segmented digest update calculations.

3. Call [digest](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-digest) to obtain the digest calculation result.

4. Call [getMdLength](../../reference/CryptoArchitectureKit/cj-apis-crypto.md#func-getmdlength) to get the digest calculation length in bytes.

### Example: Segmented Data Input to Obtain Digest Result

<!-- compile -->

```cangjie
import kit.CryptoArchitectureKit.*
import ohos.hilog.Hilog

func doLoopMd() {
    let mdAlgName = "SHA256" // Digest algorithm name.
    let md = createMd(mdAlgName)
    // Assume the total message is 43 bytes, which remains 43 bytes after UTF-8 decoding.
    let messageText = "aaaaa.....bbbbb.....ccccc.....ddddd.....eee"
    let messageData = messageText.toArray()
    let updateLength = 20 // Assume segmenting updates in 20-byte units (no actual requirement exists).
    let size = messageData.size
    for (i in 0..size : updateLength) {
        let len = if (i + updateLength > size) {
            size
        } else {
            i + updateLength
        }
        let updateMessage = messageData[i..len]
        let updateMessageBlob: DataBlob = DataBlob(updateMessage)
        md.update(updateMessageBlob)
    }
    let mdOutput = md.digest()
    Hilog.info(0,"",'[Sync]:Md result: ${mdOutput.data}')
    let mdLen = md.getMdLength()
    Hilog.info(0,"","md len: ${mdLen}")
}
```