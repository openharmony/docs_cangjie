# ohos.app.ability.ability_stage

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

AbilityStage provides functionalities related to AbilityStage, including its creation and registration.

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

- If the first line of sample code contains a "// index.cj" comment, it indicates the sample can be compiled and run in the "index.cj" file of a Cangjie template project.
- If the sample requires obtaining the [Context](./cj-apis-app-ability-ui_ability.md#class-context) application context, it needs to be configured in the "main_ability.cj" file of the Cangjie template project.

For details about the sample project and configuration template mentioned above, refer to [Cangjie Sample Code Instructions](../cj-development-intro.md#Cangjie-Sample-Code-Instructions).

## class AbilityStage

```cangjie
public open class AbilityStage {}
```

**Description:** AbilityStage is the runtime class for Ability, providing lifecycle callbacks such as creation and destruction of Ability.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### prop context

```cangjie
public mut prop context: AbilityStageContext
```

**Description:** The context of AbilityStage.

**Type:** [AbilityStageContext](cj-apis-app-ability-ui_ability.md#class-abilitystagecontext)

**Access:** Read-write

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Example:**

<!-- compile -->
```cangjie
import kit.AbilityKit.*
import ohos.business_exception.BusinessException
import kit.PerformanceAnalysisKit.Hilog

try {
    class MyAbilityStage <: AbilityStage {
        public override func onCreate(): Unit {
            let context = this.context
        }
    }
} catch (e: BusinessException) {
    Hilog.info(0, "test", "${e.message}")
}
```

### static func registerCreator(String, () -> AbilityStage)

```cangjie
public static func registerCreator(moduleName: String, creator: () -> AbilityStage): Unit
```

**Description:** Registers the creator of AbilityStage.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| moduleName | String | Yes | - | Module name. |
| creator | ()->[AbilityStage](#class-abilitystage) | Yes | - | Creator of AbilityStage. |

**Example:**

<!-- compile -->
```cangjie
import kit.AbilityKit.*
import ohos.business_exception.BusinessException
import kit.PerformanceAnalysisKit.Hilog

try {
    let ENTRY_STAGE_REGISTER_RESULT = AbilityStage.registerCreator("entry", () -> MyAbilityStage)

    class MyAbilityStage <: AbilityStage {
        public override func onCreate(): Unit {
            let context = this.context
        }
    }
} catch (e: BusinessException) {
    Hilog.info(0, "test", "${e.message}")
}
```

### func onCreate()

```cangjie
public open func onCreate(): Unit
```

**Description:** Callback when AbilityStage is created, used to execute initialization business logic operations.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Example:**

<!-- compile -->
```cangjie
import kit.AbilityKit.*
import ohos.business_exception.BusinessException
import kit.PerformanceAnalysisKit.Hilog

try {
    class MyAbilityStage <: AbilityStage {
        public override func onCreate(): Unit {
            let context = this.context
        }
    }
} catch (e: BusinessException) {
    Hilog.info(0, "test", "${e.message}")
}
```