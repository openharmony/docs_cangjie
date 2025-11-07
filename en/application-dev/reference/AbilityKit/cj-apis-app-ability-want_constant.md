# ohos.app.ability.want_constant

AbilityConstant provides enumerations related to Ability, including application launch reason LaunchReason, last exit reason LastExitReason, migration result OnContinueResult, etc.

## Import Module

```cangjie
import kit.AbilityKit.*
```

## Permission List

ohos.permission.DISTRIBUTED_DATASYNC

ohos.permission.PREPARE_APP_TERMINATE

ohos.permission.PRIVACY_WINDOW

## Usage Instructions

API sample code usage instructions:

- If the first line of sample code contains a "// index.cj" comment, it indicates the sample can be compiled and run in the "index.cj" file of the Cangjie template project.
- If the sample requires obtaining the [Context](./cj-apis-app-ability-ui_ability.md#class-context) application context, it needs to be configured in the "main_ability.cj" file of the Cangjie template project.

For details about the sample project and configuration template mentioned above, refer to [Cangjie Sample Code Description](../cj-development-intro.md#仓颉示例代码说明).

## class Flags

```cangjie
public class Flags {
    public static const FLAG_AUTH_READ_URI_PERMISSION: UInt32 = 0x00000001
    public static const FLAG_AUTH_WRITE_URI_PERMISSION: UInt32 = 0x00000002
    public static const FLAG_AUTH_PERSISTABLE_URI_PERMISSION: UInt32 = 0x00000040
    public static const FLAG_INSTALL_ON_DEMAND: UInt32 = 0x00000800
    public static const FLAG_START_WITHOUT_TIPS: UInt32 = 0x40000000
}
```

**Function:** Flags description. Used to indicate the method for processing [Want](./cj-apis-app-ability-want.md#class-want).

**System Capability:** SystemCapability.Ability.AbilityBase

**Initial Version:** 22

### static const FLAG_AUTH_PERSISTABLE_URI_PERMISSION

```cangjie
public static const FLAG_AUTH_PERSISTABLE_URI_PERMISSION: UInt32 = 0x00000040
```

**Function:** Indicates that the URI can be persisted by the recipient. This field only takes effect on tablet devices. Value: 0x00000040.

**Type:** UInt32

**System Capability:** SystemCapability.Ability.AbilityBase

**Initial Version:** 22

### static const FLAG_AUTH_READ_URI_PERMISSION

```cangjie
public static const FLAG_AUTH_READ_URI_PERMISSION: UInt32 = 0x00000001
```

**Function:** Indicates authorization to perform read operations on the URI. Value: 0x00000001.

**Type:** UInt32

**System Capability:** SystemCapability.Ability.AbilityBase

**Initial Version:** 22

### static const FLAG_AUTH_WRITE_URI_PERMISSION

```cangjie
public static const FLAG_AUTH_WRITE_URI_PERMISSION: UInt32 = 0x00000002
```

**Function:** Indicates authorization to perform write operations on the URI. Value: 0x00000002.

**Type:** UInt32

**System Capability:** SystemCapability.Ability.AbilityBase

**Initial Version:** 22

### static const FLAG_INSTALL_ON_DEMAND

```cangjie
public static const FLAG_INSTALL_ON_DEMAND: UInt32 = 0x00000800
```

**Function:** If the specified feature is not installed, install it. Value: 0x00000800.

**System Capability:** SystemCapability.Ability.AbilityBase

**Type:** UInt32

**Initial Version:** 22

### static const FLAG_START_WITHOUT_TIPS

```cangjie
public static const FLAG_START_WITHOUT_TIPS: UInt32 = 0x40000000
```

**Function:** If an implicit ability launch cannot match any application, no prompt dialog will pop up. Value: 0x40000000.

**Type:** UInt32

**System Capability:** SystemCapability.Ability.AbilityBase

**Initial Version:** 22

## class Params

```cangjie
public class Params {
    public static const ABILITY_BACK_TO_OTHER_MISSION_STACK: String = "ability.params.backToOtherMissionStack"
    public static const ABILITY_RECOVERY_RESTART: String = "ohos.ability.params.abilityRecoveryRestart"
    public static const CONTENT_TITLE_KEY: String = "ohos.extra.param.key.contentTitle"
    public static const SHARE_ABSTRACT_KEY: String = "ohos.extra.param.key.shareAbstract"
    public static const SHARE_URL_KEY: String = "ohos.extra.param.key.shareUrl"
    public static const SUPPORT_CONTINUE_PAGE_STACK_KEY: String = "ohos.extra.param.key.supportContinuePageStack"
    public static const SUPPORT_CONTINUE_SOURCE_EXIT_KEY: String = "ohos.extra.param.key.supportContinueSourceExit"
}
```

**Function:** [Want](./cj-apis-app-ability-want.md#class-want) Params operations.

**System Capability:** SystemCapability.Ability.AbilityBase

**Initial Version:** 22

### static const ABILITY_BACK_TO_OTHER_MISSION_STACK

```cangjie
public static const ABILITY_BACK_TO_OTHER_MISSION_STACK: String = "ability.params.backToOtherMissionStack"
```

**Function:** Indicates whether cross-mission stack return is supported. Value: ability.params.backToOtherMissionStack.

**Type:** String

**System Capability:** SystemCapability.Ability.AbilityBase

**Initial Version:** 22

### static const ABILITY_RECOVERY_RESTART

```cangjie
public static const ABILITY_RECOVERY_RESTART: String = "ohos.ability.params.abilityRecoveryRestart"
```

**Function:** Indicates whether the current Ability has undergone a fault recovery restart. Value: ohos.ability.params.abilityRecoveryRestart.

**Type:** String

**System Capability:** SystemCapability.Ability.AbilityBase

**Initial Version:** 22

### static const CONTENT_TITLE_KEY

```cangjie
public static const CONTENT_TITLE_KEY: String = "ohos.extra.param.key.contentTitle"
```

**Function:** Indicates the operation parameter for sharing titles supported by meta services. Value: ohos.extra.param.key.contentTitle.

**Type:** String

**System Capability:** SystemCapability.Ability.AbilityBase

**Initial Version:** 22

### static const SHARE_ABSTRACT_KEY

```cangjie
public static const SHARE_ABSTRACT_KEY: String = "ohos.extra.param.key.shareAbstract"
```

**Function:** Indicates the page source file. Value: ohos.param.atomicservice.pageSourceFile.

**Type:** String

**System Capability:** SystemCapability.Ability.AbilityBase

**Initial Version:** 22

### static const SHARE_URL_KEY

```cangjie
public static const SHARE_URL_KEY: String = "ohos.extra.param.key.shareUrl"
```

**Function:** Indicates the operation parameter for sharing content supported by meta services. Value: ohos.extra.param.key.shareAbstract.

**Type:** String

**System Capability:** SystemCapability.Ability.AbilityBase

**Initial Version:** 22

### static const SUPPORT_CONTINUE_PAGE_STACK_KEY

```cangjie
public static const SUPPORT_CONTINUE_PAGE_STACK_KEY: String = "ohos.extra.param.key.supportContinuePageStack"
```

**Function:** Indicates whether to migrate page stack information during cross-device migration. The default value is true, meaning page stack information is automatically migrated. Value: ohos.extra.param.key.supportContinuePageStack.

**Type:** String

**System Capability:** SystemCapability.Ability.AbilityBase

**Initial Version:** 22

### static const SUPPORT_CONTINUE_SOURCE_EXIT_KEY

```cangjie
public static const SUPPORT_CONTINUE_SOURCE_EXIT_KEY: String = "ohos.extra.param.key.supportContinueSourceExit"
```

**Function:** Indicates whether the source application exits during cross-device migration. The default value is true, meaning the source application exits automatically. Value: ohos.extra.param.key.supportContinueSourceExit.

**Type:** String

**System Capability:** SystemCapability.Ability.AbilityBase

**Initial Version:** 22
