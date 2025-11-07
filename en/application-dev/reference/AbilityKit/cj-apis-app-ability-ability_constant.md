# ohos.app.ability.ability_constant

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

For details about the above sample project and configuration template, see [Cangjie Sample Code Description](../cj-development-intro.md#Cangjie-Sample-Code-Description).

## class LaunchParam

```cangjie
public class LaunchParam {
    public var launchReason: LaunchReason
    public var lastExitReason: LastExitReason
}
```

**Function:** Launch parameters, including launch reason and last exit reason.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### var lastExitReason

```cangjie
public var lastExitReason: LastExitReason
```

**Function:** Last exit reason.

**Type:** [LastExitReason](#enum-lastexitreason)

**Read/Write:** Readable and Writable

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### var launchReason

```cangjie
public var launchReason: LaunchReason
```

**Function:** Launch reason.

**Type:** [LaunchReason](#enum-launchreason)

**Read/Write:** Readable and Writable

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

## enum LastExitReason

```cangjie
public enum LastExitReason {
    | Unknown
    | Normal
    | CppCrash
    | AppFreeze
    | ...
}
```

**Function:** Last exit reason.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### AppFreeze

```cangjie
AppFreeze
```

**Function:** Application freeze.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### CppCrash

```cangjie
CppCrash
```

**Function:** C++ crash.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### Normal

```cangjie
Normal
```

**Function:** Normal exit.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### Unknown

```cangjie
Unknown
```

**Function:** Unknown reason.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

## enum LaunchReason

```cangjie
public enum LaunchReason {
    | Unknown
    | StartAbility
    | Call
    | Continuation
    | AppRecovery
    | ...
}
```

**Function:** Launch reason.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### AppRecovery

```cangjie
AppRecovery
```

**Function:** Application recovery.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### Call

```cangjie
Call
```

**Function:** Call launch.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### Continuation

```cangjie
Continuation
```

**Function:** Cross-device migration.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### StartAbility

```cangjie
StartAbility
```

**Function:** Start Ability.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### Unknown

```cangjie
Unknown
```

**Function:** Unknown reason.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

## enum MemoryLevel

```cangjie
public enum MemoryLevel <: Equatable<MemoryLevel> & ToString {
    | MemoryLevelModerate
    | MemoryLevelLow
    | MemoryLevelCritical
    | ...
}
```

**Function:** Memory level.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Parent Types:**

- [Equatable\<MemoryLevel>](#enum-memorylevel)
- ToString

### MemoryLevelCritical

```cangjie
MemoryLevelCritical
```

**Function:** Critical memory shortage.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### MemoryLevelLow

```cangjie
MemoryLevelLow
```

**Function:** Low memory.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### MemoryLevelModerate

```cangjie
MemoryLevelModerate
```

**Function:** Moderate memory.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### func !=(MemoryLevel)

```cangjie
public operator func !=(other: MemoryLevel): Bool
```

**Function:** Determines whether two enumeration values are not equal.

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| other | [MemoryLevel](#enum-memorylevel) | Yes | - | Another enumeration value. |

**Return Value:**

| Type | Description |
|:----|:----|
| Bool | Returns true if the two enumeration values are not equal, otherwise returns false. |

### func ==(MemoryLevel)

```cangjie
public operator func ==(other: MemoryLevel): Bool
```

**Function:** Determines whether two enumeration values are equal.

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| other | [MemoryLevel](#enum-memorylevel) | Yes | - | Another enumeration value. |

**Return Value:**

| Type | Description |
|:----|:----|
| Bool | Returns true if the two enumeration values are equal, otherwise returns false. |

### func toString()

```cangjie
public func toString(): String
```

**Function:** Gets the string representation of the current enumeration.

**Return Value:**

| Type | Description |
|:----|:----|
| String | The string representation of the current enumeration. |

## enum OnContinueResult

```cangjie
public enum OnContinueResult {
    | Agree
    | Reject
    | Mismatch
    | ...
}
```

**Function:** Cross-device migration result.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### Agree

```cangjie
Agree
```

**Function:** Agree to migrate.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### Mismatch

```cangjie
Mismatch
```

**Function:** Migration mismatch.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### Reject

```cangjie
Reject
```

**Function:** Reject migration.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

## enum WindowMode

```cangjie
public enum WindowMode {
    | WindowModeFullscreen
    | WindowModeSplitPrimary
    | WindowModeSplitSecondary
    | ...
}
```

**Function:** Window mode.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22### WindowModeFullscreen

```cangjie
WindowModeFullscreen
```

**Function:** Fullscreen mode.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since Version:** 22

### WindowModeSplitPrimary

```cangjie
WindowModeSplitPrimary
```

**Function:** Primary split-screen window.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since Version:** 22

### WindowModeSplitSecondary

```cangjie
WindowModeSplitSecondary
```

**Function:** Secondary split-screen window.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since Version:** 22