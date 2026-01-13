# ohos.metadata

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

This module describes metadata information.

## Importing the Module

```cangjie
import kit.AbilityKit.*
```

## Usage Instructions

API sample code usage instructions:

- If the sample code has a "// index.cj" comment in its first line, it indicates that the example can be compiled and run in the "index.cj" file of the Cangjie template project.
- If the sample requires obtaining the [Context](./cj-apis-app-ability-ui_ability.md#class-context) application context, it needs to be configured in the "main_ability.cj" file of the Cangjie template project.

For the aforementioned sample projects and configuration templates, please refer to [Cangjie Sample Code Instructions](../cj-development-intro.md#Cangjie-Sample-Code-Instructions).

## class Metadata

```cangjie
public class Metadata {
    public var name: String
    public var value: String
    public var resource: String
}
```

**Function:** Metadata information. Obtained by calling the [getBundleInfoForSelf](./cj-apis-bundle_manager.md#static-func-getbundleinfoforselfint32) interface, with the bundleFlags parameter passing the values of GET_BUNDLE_INFO_WITH_HAP_MODULE, GET_BUNDLE_INFO_WITH_ABILITY, and GET_BUNDLE_INFO_WITH_METADATA.

**System Capability:** SystemCapability.BundleManager.BundleFramework.Core

**Initial Version:** 22

### var name

```cangjie
public var name: String
```

**Function:** Metadata name.

**Type:** String

**Read/Write Capability:** Readable and Writable

**System Capability:** SystemCapability.BundleManager.BundleFramework.Core

**Initial Version:** 22

### var resource

```cangjie
public var resource: String
```

**Function:** Metadata resource.

**Type:** String

**Read/Write Capability:** Readable and Writable

**System Capability:** SystemCapability.BundleManager.BundleFramework.Core

**Initial Version:** 22

### var value

```cangjie
public var value: String
```

**Function:** Metadata value.

**Type:** String

**Read/Write Capability:** Readable and Writable

**System Capability:** SystemCapability.BundleManager.BundleFramework.Core

**Initial Version:** 22