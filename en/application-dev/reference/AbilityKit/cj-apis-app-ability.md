# ohos.app.ability

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

The Ability module provides definitions including the BaseContext class.

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

- If the sample code's first line contains a "// index.cj" comment, it indicates the sample can be compiled and run in the "index.cj" file of the Cangjie template project.
- If the sample requires obtaining the [Context](./cj-apis-app-ability-ui_ability.md#class-context) application context, it needs to be configured in the "main_ability.cj" file of the Cangjie template project.

For the aforementioned sample projects and configuration templates, please refer to [Cangjie Sample Code Instructions](../cj-development-intro.md#仓颉示例代码说明).

## class BaseContext

```cangjie
public abstract class BaseContext {
    public let stageMode: Bool
}
```

**Function:** Provides context capabilities for ability or application.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### let stageMode

```cangjie
public let stageMode: Bool
```

**Function:** Indicates whether it's Stage model.

**Type:** Bool

**Access:** Read-only

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Example:**

<!-- compile -->
```cangjie
import kit.AbilityKit.*

class MyUIAbility <: UIAbility {
    public override func onWindowStageCreate(windowStage: WindowStage): Unit {
          let isStageMode = this.context.stageMode
    }
}
```