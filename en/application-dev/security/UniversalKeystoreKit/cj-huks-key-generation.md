# Generating Keys (Cangjie)

Taking the generation of DH keys as an example, this section describes how to generate random keys. For specific scenarios and supported algorithm specifications, refer to [Supported Algorithms for Key Generation](./cj-huks-key-generation-overview.md#supported-algorithms).

> **Note:**
>
> Sensitive information such as personal data is prohibited in key aliases.

## Development Steps

1. Specify the key alias `keyAlias` to be generated.

    - The maximum length of a key alias is 128 bytes. It is recommended to avoid sensitive terms such as personal information.
    - For keys generated across different services, HUKS will isolate storage paths based on service identity information, preventing conflicts due to identical key names in different services.

2. Initialize the key property set. Encapsulate key properties via [HuksParam](../../reference/UniversalKeystoreKit/cj-apis-security_huks.md#class-huksparam), combine them into a property set using an Array, and assign them to the `properties` field in [HuksOptions](../../reference/UniversalKeystoreKit/cj-apis-security_huks.md#class-huksoptions).

    The key property set must include the [HuksKeyAlg](../../reference/UniversalKeystoreKit/cj-apis-security_huks.md#class-hukskeyalg), [HuksKeySize](../../reference/UniversalKeystoreKit/cj-apis-security_huks.md#class-hukskeysize), and [HuksKeyPurpose](../../reference/UniversalKeystoreKit/cj-apis-security_huks.md#class-hukskeypurpose) attributes, i.e., the mandatory tags: `HUKS_TAG_ALGORITHM`, `HUKS_TAG_PURPOSE`, and `HUKS_TAG_KEY_SIZE`. Note: A key can only have one type of PURPOSE, and the purpose specified during key generation must match the usage method; otherwise, exceptions may occur.

3. Call [generateKeyItem](../../reference/UniversalKeystoreKit/cj-apis-security_huks.md#func-generatekeyitemstring-huksoptions), passing the key alias and key property set to generate the key.

> **Note:**
>
> If a service calls HUKS again with the same alias to generate a key, HUKS will generate a new key and directly overwrite the historical key file.

## Example

<!-- compile -->

```cangjie
/* Example of generating a DH key */
import kit.PerformanceAnalysisKit.Hilog
import kit.BasicServicesKit.*
import kit.CoreFileKit.*
import kit.AbilityKit.*
import kit.UniversalKeystoreKit.*

func loggerInfo(str: String) {
    Hilog.info(0, "CangjieTest", str)
}

/* 1. Determine the key alias */
let keyAlias = 'dh_key'
/* 2. Initialize the key property set */
let properties1: Array<HuksParam> = [
  HuksParam(
    HuksTag.HUKS_TAG_ALGORITHM,
    HuksParamValue.Uint32Value(HuksKeyAlg.HUKS_ALG_DH)
  ),
  HuksParam(
    HuksTag.HUKS_TAG_PURPOSE,
    HuksParamValue.Uint32Value(HuksKeyPurpose.HUKS_KEY_PURPOSE_AGREE)
  ),
  HuksParam(
    HuksTag.HUKS_TAG_KEY_SIZE,
    HuksParamValue.Uint32Value(HuksKeySize.HUKS_DH_KEY_SIZE_2048)
  )
]
let huksOptions: HuksOptions = HuksOptions(
  properties: properties1,
  inData: Bytes()
)

/* 3. Generate the key */
func publicGenKeyFunc(keyAlias: String, huksOptions: HuksOptions) {
  loggerInfo("enter generateKeyItem")
  try {
    generateKeyItem(keyAlias, huksOptions)
  } catch (e: Exception) {
    loggerInfo("generateKeyItem input arg invalid, ${e}")
  }
}

func TestGenKey() {
  publicGenKeyFunc(keyAlias, huksOptions)
}
```