# ohos.app.ability.want_constant

AbilityConstant提供Ability相关的枚举，包括应用启动原因LaunchReason、上次退出原因LastExitReason、迁移结果OnContinueResult等。

## 导入模块

```cangjie
import kit.AbilityKit.*
```

## 权限列表

ohos.permission.DISTRIBUTED_DATASYNC

ohos.permission.PREPARE_APP_TERMINATE

ohos.permission.PRIVACY_WINDOW

## 使用说明

API示例代码使用说明：

- 若示例代码首行有"// index.cj"注释，表示该示例可在仓颉模板工程的"index.cj"文件中编译运行。
- 若示例需获取[Context](./cj-apis-app-ability-ui_ability.md#class-context)应用上下文，需在仓颉模板工程中的"main_ability.cj"文件中进行配置。

上述示例工程及配置模板详见[仓颉示例代码说明](../cj-development-intro.md#仓颉示例代码说明)。

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

**功能：** Flags说明。用于表示处理[Want](./cj-apis-app-ability-want.md#class-want)的方式。

**系统能力：** SystemCapability.Ability.AbilityBase

**起始版本：** 22

### static const FLAG_AUTH_PERSISTABLE_URI_PERMISSION

```cangjie
public static const FLAG_AUTH_PERSISTABLE_URI_PERMISSION: UInt32 = 0x00000040
```

**功能：** 指示该URI可被接收方持久化。该字段仅在平板类设备上生效。值为：0x00000040。

**类型：** UInt32

**系统能力：** SystemCapability.Ability.AbilityBase

**起始版本：** 22

### static const FLAG_AUTH_READ_URI_PERMISSION

```cangjie
public static const FLAG_AUTH_READ_URI_PERMISSION: UInt32 = 0x00000001
```

**功能：** 指示对URI执行读取操作的授权。值为：0x00000001。

**类型：** UInt32

**系统能力：** SystemCapability.Ability.AbilityBase

**起始版本：** 22

### static const FLAG_AUTH_WRITE_URI_PERMISSION

```cangjie
public static const FLAG_AUTH_WRITE_URI_PERMISSION: UInt32 = 0x00000002
```

**功能：** 指示对URI执行写入操作的授权。值为：0x00000002。

**类型：** UInt32

**系统能力：** SystemCapability.Ability.AbilityBase

**起始版本：** 22

### static const FLAG_INSTALL_ON_DEMAND

```cangjie
public static const FLAG_INSTALL_ON_DEMAND: UInt32 = 0x00000800
```

**功能：** 如果未安装指定的功能，请安装该功能。值为：0x00000800。

**类型：** UInt32

**系统能力：** SystemCapability.Ability.AbilityBase

**起始版本：** 22

### static const FLAG_START_WITHOUT_TIPS

```cangjie
public static const FLAG_START_WITHOUT_TIPS: UInt32 = 0x40000000
```

**功能：** 如果隐式启动能力不能匹配任何应用程序，则不会弹出提示对话框。值为：0x40000000。

**类型：** UInt32

**系统能力：** SystemCapability.Ability.AbilityBase

**起始版本：** 22

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

**功能：** [Want](./cj-apis-app-ability-want.md#class-want)的Params操作。

**系统能力：** SystemCapability.Ability.AbilityBase

**起始版本：** 22

### static const ABILITY_BACK_TO_OTHER_MISSION_STACK

```cangjie
public static const ABILITY_BACK_TO_OTHER_MISSION_STACK: String = "ability.params.backToOtherMissionStack"
```

**功能：** 表示是否支持跨任务链返回。值为：ability.params.backToOtherMissionStack。

**类型：** String

**系统能力：** SystemCapability.Ability.AbilityBase

**起始版本：** 22

### static const ABILITY_RECOVERY_RESTART

```cangjie
public static const ABILITY_RECOVERY_RESTART: String = "ohos.ability.params.abilityRecoveryRestart"
```

**功能：** 指示当前Ability是否发生了故障恢复重启。值为：ohos.ability.params.abilityRecoveryRestart。

**类型：** String

**系统能力：** SystemCapability.Ability.AbilityBase

**起始版本：** 22

### static const CONTENT_TITLE_KEY

```cangjie
public static const CONTENT_TITLE_KEY: String = "ohos.extra.param.key.contentTitle"
```

**功能：** 指示元服务支持分享标题的参数的操作。值为：ohos.extra.param.key.contentTitle。

**类型：** String

**系统能力：** SystemCapability.Ability.AbilityBase

**起始版本：** 22

### static const SHARE_ABSTRACT_KEY

```cangjie
public static const SHARE_ABSTRACT_KEY: String = "ohos.extra.param.key.shareAbstract"
```

**功能：** 指示页面源文件。值为：ohos.param.atomicservice.pageSourceFile。

**类型：** String

**系统能力：** SystemCapability.Ability.AbilityBase

**起始版本：** 22

### static const SHARE_URL_KEY

```cangjie
public static const SHARE_URL_KEY: String = "ohos.extra.param.key.shareUrl"
```

**功能：** 指示元服务支持分享内容的参数的操作。值为：ohos.extra.param.key.shareAbstract。

**类型：** String

**系统能力：** SystemCapability.Ability.AbilityBase

**起始版本：** 22

### static const SUPPORT_CONTINUE_PAGE_STACK_KEY

```cangjie
public static const SUPPORT_CONTINUE_PAGE_STACK_KEY: String = "ohos.extra.param.key.supportContinuePageStack"
```

**功能：** 指示在跨端迁移过程中是否迁移页面栈信息，默认值为true，自动迁移页面栈信息。值为：ohos.extra.param.key.supportContinuePageStack。

**类型：** String

**系统能力：** SystemCapability.Ability.AbilityBase

**起始版本：** 22

### static const SUPPORT_CONTINUE_SOURCE_EXIT_KEY

```cangjie
public static const SUPPORT_CONTINUE_SOURCE_EXIT_KEY: String = "ohos.extra.param.key.supportContinueSourceExit"
```

**功能：** 指示跨端迁移源端应用是否退出，默认值为true，源端应用自动退出。值为：ohos.extra.param.key.supportContinueSourceExit。

**类型：** String

**系统能力：** SystemCapability.Ability.AbilityBase

**起始版本：** 22
