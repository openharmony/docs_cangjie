# ohos.skill

This module introduces the Skill tag object.

## Import Module

```cangjie
import kit.AbilityKit.*
```

## Usage Instructions

API sample code usage instructions:

- If the first line of sample code contains a "// index.cj" comment, it indicates the sample can be compiled and run in the "index.cj" file of the Cangjie template project.
- If the sample requires obtaining the [Context](./cj-apis-app-ability-ui_ability.md#class-context) application context, it needs to be configured in the "main_ability.cj" file of the Cangjie template project.

For details about the aforementioned sample project and configuration template, refer to [Cangjie Sample Code Instructions](../cj-development-intro.md#仓颉示例代码说明).

## Usage Instructions

API sample code usage instructions:

- If the first line of sample code contains a "// index.cj" comment, it indicates the sample can be compiled and run in the "index.cj" file of the Cangjie template project.
- If the sample requires obtaining the [Context](./cj-apis-app-ability-ui_ability.md#class-context) application context, it needs to be configured in the "main_ability.cj" file of the Cangjie template project.

For details about the aforementioned sample project and configuration template, refer to [Cangjie Sample Code Instructions](../cj-development-intro.md#仓颉示例代码说明).

## class Skill

```cangjie
public class Skill {
    public let actions: Array<String>
    public let entities: Array<String>
    public let uris: Array<SkillUri>
    public let domainVerify: Bool
}
```

**Function:** The Skill tag object. Third-party applications can obtain Skill information through [getBundleInfoForSelf](./cj-apis-bundle_manager.md#static-func-getbundleinfoforselfint32), where the input parameter bundleFlags must include GET_BUNDLE_INFO_WITH_HAP_MODULE, GET_BUNDLE_INFO_WITH_ABILITY, and GET_BUNDLE_INFO_WITH_SKILL.

**System Capability:** SystemCapability.BundleManager.BundleFramework.Core

**Initial Version:** 22

### let actions

```cangjie
public let actions: Array<String>
```

**Function:** The collection of Actions received by the Skill.

**Type:** Array\<String>

**Read-Write Attributes:** Read-only

**System Capability:** SystemCapability.BundleManager.BundleFramework.Core

**Initial Version:** 22

### let domainVerify

```cangjie
public let domainVerify: Bool
```

**Function:** The DomainVerify value received by the Skill, only existing in AbilityInfo.

**Type:** Bool

**Read-Write Attributes:** Read-only

**System Capability:** SystemCapability.BundleManager.BundleFramework.Core

**Initial Version:** 22

### let entities

```cangjie
public let entities: Array<String>
```

**Function:** The collection of Entities received by the Skill.

**Type:** Array\<String>

**Read-Write Attributes:** Read-only

**System Capability:** SystemCapability.BundleManager.BundleFramework.Core

**Initial Version:** 22

### let uris

```cangjie
public let uris: Array<SkillUri>
```

**Function:** The collection of URIs for Want matching.

**Type:** Array\<[SkillUri](#class-skilluri)>

**Read-Write Attributes:** Read-only

**System Capability:** SystemCapability.BundleManager.BundleFramework.Core

**Initial Version:** 22

## class SkillUri

```cangjie
public class SkillUri {
    public let scheme: String
    public let host: String
    public let port: Int32
    public let path: String
    public let pathStartWith: String
    public let pathRegex: String
    public let uriType: String
    public let utd: String
    public let maxFileSupported: Int32
    public let linkFeature: String
}
```

**Function:** Describes URI identification information.

**System Capability:** SystemCapability.BundleManager.BundleFramework.Core

**Initial Version:** 22

### let host

```cangjie
public let host: String
```

**Function:** Identifies the host address part of the URI, meaningful only when scheme exists.

**Type:** String

**Read-Write Attributes:** Read-only

**System Capability:** SystemCapability.BundleManager.BundleFramework.Core

**Initial Version:** 22

### let linkFeature

```cangjie
public let linkFeature: String
```

**Function:** Identifies the feature type provided by the URI, used for inter-application jumps, only existing in AbilityInfo.

**Type:** String

**Read-Write Attributes:** Read-only

**System Capability:** SystemCapability.BundleManager.BundleFramework.Core

**Initial Version:** 22

### let maxFileSupported

```cangjie
public let maxFileSupported: Int32
```

**Function:** For specified file types, identifies the maximum number of files that can be received or opened at once.

**Type:** Int32

**Read-Write Attributes:** Read-only

**System Capability:** SystemCapability.BundleManager.BundleFramework.Core

**Initial Version:** 22

### let path

```cangjie
public let path: String
```

**Function:** Identifies the path part of the URI, meaningful only when both scheme and host exist.

**Type:** String

**Read-Write Attributes:** Read-only

**System Capability:** SystemCapability.BundleManager.BundleFramework.Core

**Initial Version:** 22

### let pathRegex

```cangjie
public let pathRegex: String
```

**Function:** Identifies the path part of the URI for regular expression matching, meaningful only when both scheme and host exist.

**Type:** String

**Read-Write Attributes:** Read-only

**System Capability:** SystemCapability.BundleManager.BundleFramework.Core

**Initial Version:** 22

### let pathStartWith

```cangjie
public let pathStartWith: String
```

**Function:** Identifies the path part of the URI for prefix matching, meaningful only when both scheme and host exist.

**Type:** String

**Read-Write Attributes:** Read-only

**System Capability:** SystemCapability.BundleManager.BundleFramework.Core

**Initial Version:** 22

### let port

```cangjie
public let port: Int32
```

**Function:** Identifies the port part of the URI, meaningful only when both scheme and host exist.

**Type:** Int32

**Read-Write Attributes:** Read-only

**System Capability:** SystemCapability.BundleManager.BundleFramework.Core

**Initial Version:** 22

### let scheme

```cangjie
public let scheme: String
```

**Function:** Identifies the protocol name of the URI, common examples include http, https, file, ftp, etc.

**Type:** String

**Read-Write Attributes:** Read-only

**System Capability:** SystemCapability.BundleManager.BundleFramework.Core

**Initial Version:** 22

### let uriType

```cangjie
public let uriType: String
```

**Function:** Identifies the data type matching the Want, using the MIME (Multipurpose Internet Mail Extensions) type specification.

**Type:** String

**Read-Write Attributes:** Read-only

**System Capability:** SystemCapability.BundleManager.BundleFramework.Core

**Initial Version:** 22

### let utd

```cangjie
public let utd: String
```

**Function:** Identifies the standardized data type of the URI matching the Want, applicable to scenarios such as sharing.

**Type:** String

**Read-Write Attributes:** Read-only

**System Capability:** SystemCapability.BundleManager.BundleFramework.Core

**Initial Version:** 22