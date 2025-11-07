# Check If a Key Exists (Cangjie)

HUKS provides interfaces for applications to check whether a specified key exists.

## Development Procedure

1. Specify the key alias `keyAlias`. The maximum length of a key alias is 128 bytes.

2. Initialize the key property set. Used to specify [key property TAGs](../../reference/UniversalKeystoreKit/cj-apis-security_huks.md#class-huksoptions) during queries. When querying a single key, the TAG field can be empty.

3. Call the [isKeyItemExist](../../reference/UniversalKeystoreKit/cj-apis-security_huks.md#func-iskeyitemexiststring-huksoptions) interface to check whether the key exists.

## Example

<!-- compile -->

```cangjie
import kit.PerformanceAnalysisKit.Hilog
import kit.BasicServicesKit.*
import kit.CoreFileKit.*
import kit.AbilityKit.*
import kit.UniversalKeystoreKit.*

/* 1. Determine the key alias */
let keyAlias = "test_is_key_item_exist"

/* 2. Check if the key exists; variable a should be false */
var a = isKeyItemExist(keyAlias, HuksOptions())

let options = HuksOptions(
    properties: [
        
        (HuksTag.HUKS_TAG_ALGORITHM, HuksParamValue.Uint32Value(HuksKeyAlg.HUKS_ALG_AES)),
        HuksParam(
            HuksTag.HUKS_TAG_KEY_SIZE, 
            HuksParamValue.Uint32Value(HuksKeySize.HUKS_AES_KEY_SIZE_128)
        ),
        HuksParam(
            HuksTag.HUKS_TAG_PURPOSE,
            HuksParamValue.Uint32Value(1 | 2)
        )
    ],
    inData: Bytes()
)

/* 3. Generate the key */
generateKeyItem(keyAlias, options)
/* 4. Check if the key exists; variable a should now be true */
a = isKeyItemExist(keyAlias, HuksOptions())
```