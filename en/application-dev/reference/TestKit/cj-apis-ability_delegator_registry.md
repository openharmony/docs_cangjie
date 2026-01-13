# ohos.app.ability.ability_delegator_registry

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

The AbilityDelegatorRegistry module provides the capability to store registered [AbilityDelegator](#class-abilitydelegator) and [AbilityDelegatorArgs](#class-abilitydelegatorargs) objects in a global registry, including obtaining the application's [AbilityDelegator](#class-abilitydelegator) object and unit test parameter objects. The interfaces in this module can only be used within test frameworks.

## Import Module

```cangjie
import kit.TestKit.*
```

## Usage Instructions

API sample code usage instructions:

- If the first line of sample code contains a "// index.cj" comment, it indicates that the example can be compiled and run in the "index.cj" file of the Cangjie template project.
- If the sample requires obtaining the [Context](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-context) application context, it needs to be configured in the "main_ability.cj" file of the Cangjie template project.

For the above sample project and configuration template details, refer to [Cangjie Sample Code Instructions](../cj-development-intro.md#仓颉示例代码说明).

## class AbilityDelegator

```cangjie
public class AbilityDelegator {}
```

**Description:** AbilityDelegator is used to create and manage an [AbilityMonitor](#class-abilitymonitor) object (which monitors lifecycle state changes of a specified [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability)), including adding and removing [AbilityMonitor](#class-abilitymonitor) instances, waiting for [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) to reach the OnCreate lifecycle, setting wait time, obtaining the lifecycle state of a specified Ability, obtaining the top [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) of the current application, and starting a specified [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability).

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### func addAbilityMonitor(AbilityMonitor)

```cangjie
public func addAbilityMonitor(monitor: AbilityMonitor): Unit
```

**Description:** Adds an [AbilityMonitor](#class-abilitymonitor) instance. Concurrent calls from multiple threads are not supported.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Parameters:**

| Name | Type | Mandatory | Default Value | Description |
| :--- | :--- | :--- | :--- | :--- |
| monitor | [AbilityMonitor](#class-abilitymonitor) | Yes | - | [AbilityMonitor](#class-abilitymonitor) instance. |

**Exceptions:**

For detailed error codes, refer to [Ability Subsystem Error Codes](../AbilityKit/cj-errorcode-ability.md).

  | Error Code ID | Error Message |
  | :--- | :--- |
  | 16000100 | AddAbilityMonitor failed. |

**Example:**

<!-- compile -->

```cangjie
// index.cj

import kit.AbilityKit.*
import kit.TestKit.*

let delegator = AbilityDelegatorRegistry.getAbilityDelegator()
let monitor = AbilityMonitor(
        "EntryAbility", moduleName: "entry",
        onAbilityCreate: {ability => delegator.print("onAbilityCreate called, abilityName: ${ability.launchWant.abilityName}")}
)
delegator.addAbilityMonitor(monitor)
```

### func addAbilityStageMonitor(AbilityStageMonitor)

```cangjie
public func addAbilityStageMonitor(monitor: AbilityStageMonitor): Unit
```

**Description:** Adds an [AbilityStageMonitor](#class-abilitystagemonitor) object to monitor lifecycle state changes of a specified [AbilityStage](../AbilityKit/cj-apis-app-ability-ability_stage.md#class-abilitystage).

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Parameters:**

| Name | Type | Mandatory | Default Value | Description |
| :--- | :--- | :--- | :--- | :--- |
| monitor | [AbilityStageMonitor](#class-abilitystagemonitor) | Yes | - | [AbilityStageMonitor](#class-abilitystagemonitor) instance. |

**Exceptions:**

For detailed error codes, refer to [Ability Subsystem Error Codes](../AbilityKit/cj-errorcode-ability.md).

  | Error Code ID | Error Message |
  | :--- | :--- |
  | 16000100 | AddAbilityStageMonitor failed. |

**Example:**

<!-- compile -->

```cangjie
// index.cj

import kit.AbilityKit.*
import kit.TestKit.*

let delegator = AbilityDelegatorRegistry.getAbilityDelegator()
let monitor = AbilityStageMonitor("entry", "ohos_app_cangjie_entry.MyAbilityStage")
delegator.addAbilityStageMonitor(monitor)
```

### func doAbilityBackground(UIAbility)

```cangjie
public func doAbilityBackground(ability: UIAbility): Unit
```

**Description:** Schedules the lifecycle state of a specified [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) to the Background state.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Parameters:**

| Name | Type | Mandatory | Default Value | Description |
| :--- | :--- | :--- | :--- | :--- |
| ability | [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) | Yes | - | [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) object. |

**Exceptions:**

For detailed error codes, refer to [Ability Subsystem Error Codes](../AbilityKit/cj-errorcode-ability.md).

  | Error Code ID | Error Message |
  | :--- | :--- |
  | 16000100 | DoAbilityBackground failed. |

**Example:**

<!-- compile -->

```cangjie
// index.cj

import kit.AbilityKit.*
import kit.TestKit.*

let delegator = AbilityDelegatorRegistry.getAbilityDelegator()
let ability = delegator.getCurrentTopAbility()
delegator.doAbilityBackground(ability)
```

### func doAbilityForeground(UIAbility)

```cangjie
public func doAbilityForeground(ability: UIAbility): Unit
```

**Description:** Schedules the lifecycle state of a specified [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) to the Foreground state.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Parameters:**

| Name | Type | Mandatory | Default Value | Description |
| :--- | :--- | :--- | :--- | :--- |
| ability | [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) | Yes | - | [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) object. |

**Exceptions:**

For detailed error codes, refer to [Ability Subsystem Error Codes](../AbilityKit/cj-errorcode-ability.md).

  | Error Code ID | Error Message |
  | :--- | :--- |
  | 16000100 | DoAbilityForeground failed. |

**Example:**

<!-- compile -->

```cangjie
// index.cj

import kit.AbilityKit.*
import kit.TestKit.*

let delegator = AbilityDelegatorRegistry.getAbilityDelegator()
let ability = delegator.getCurrentTopAbility()
delegator.doAbilityForeground(ability)
```

### func executeShellCommand(String, Int64)

```cangjie
public func executeShellCommand(ccmd: String, timeoutSecs!: Int64 = 0): ShellCmdResult
```

**Description:** Executes the specified Shell command.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Parameters:**

| Name | Type | Mandatory | Default Value | Description |
| :--- | :--- | :--- | :--- | :--- |
| cmd | String | Yes | - | Shell command string. |
| timeoutSecs | Int64 | No | 0 | Sets the command timeout period in seconds (s). |

**Return Value:**

| Type | Description |
| :---- | :---- |
| [ShellCmdResult](#class-shellcmdresult) | Returns the Shell command execution result as a [ShellCmdResult](#class-shellcmdresult) object. |

**Example:**

<!-- compile -->

```cangjie
// index.cj

import kit.AbilityKit.*
import kit.TestKit.*

let delegator = AbilityDelegatorRegistry.getAbilityDelegator()
let cmd = "cmd"
delegator.executeShellCommand(cmd, timeoutSecs: 2)
```

### func finishTest(String, Int64)

```cangjie
public func finishTest(msg: String, code: Int64): Unit
```

**Description:** Ends the test and prints log information to the unit test terminal console.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Parameters:**

| Name | Type | Mandatory | Default Value | Description |
| :--- | :--- | :--- | :--- | :--- |
| msg | String | Yes | - | Log string. |
| code | Int64 | Yes | - | Log code. |

**Example:**

<!-- compile -->

```cangjie
// index.cj

import kit.AbilityKit.*
import kit.TestKit.*

let delegator = AbilityDelegatorRegistry.getAbilityDelegator()
let msg = "msg"
delegator.finishTest(msg, 0)
```

### func getAbilityState(UIAbility)

```cangjie
public func getAbilityState(ability: UIAbility): AbilityLifecycleState
```

**Description:** Gets the lifecycle state of the specified ability.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Parameters:**

| Name | Type | Mandatory | Default Value | Description |
| :--- | :--- | :--- | :--- | :--- |
| ability | [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) | Yes | - | Specified [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) object. |

**Return Value:**

| Type | Description |
| :---- | :---- |
| [AbilityLifecycleState](#enum-abilitylifecyclestate) | Lifecycle state of the specified ability. |

**Exceptions:**

For detailed error codes, refer to [Universal Error Codes](../cj-errorcode-universal.md).

  | Error Code ID | Error Message |
  | :--- | :--- |
  | 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example:**

<!-- compile -->

```cangjie
// index.cj

import kit.AbilityKit.*
import kit.TestKit.*

let delegator = AbilityDelegatorRegistry.getAbilityDelegator()
let ability = delegator.getCurrentTopAbility()
delegator.getAbilityState(ability)
```

### func getAppContext()

```cangjie
public func getAppContext(): Context
```

**Description:** Gets the application Context.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Return Value:**

| Type | Description |
| :---- | :---- |
| [Context](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-context) | Application Context. |

**Example:**

<!-- compile -->

```cangjie
// index.cj

import kit.AbilityKit.*
import kit.TestKit.*

let delegator = AbilityDelegatorRegistry.getAbilityDelegator()
let context = delegator.getAppContext()
```

### func getCurrentTopAbility()

```cangjie
public func getCurrentTopAbility(): UIAbility
```

**Description:** Gets the top [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) of the current application.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Return Value:**

| Type | Description |
| :---- | :---- |
| [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) | Returns the [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) instance. |

**Exceptions:**

For detailed error codes, refer to [Ability Subsystem Error Codes](../AbilityKit/cj-errorcode-ability.md).

  | Error Code ID | Error Message |
  | :--- | :--- |
  | 16000100 | GetCurrentTopAbility failed. |

**Example:**

<!-- compile -->

```cangjie
// index.cj

import kit.AbilityKit.*
import kit.TestKit.*

let delegator = AbilityDelegatorRegistry.getAbilityDelegator()
let ability = delegator.getCurrentTopAbility()
delegator.getAbilityState(ability)
```

### func print(String)

```cangjie
public func print(msg: String): Unit
```

**Description:** Prints log information to the unit test terminal console.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Parameters:**

| Name | Type | Mandatory | Default Value | Description |
| :--- | :--- | :--- | :--- | :--- |
| msg | String | Yes | - | Log string. |

**Exceptions:**

For detailed error codes, refer to [Universal Error Codes](../cj-errorcode-universal.md).

  | Error Code ID | Error Message |
  | :--- | :--- |
  | 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example:**

<!-- compile -->

```cangjie
// index.cj

import kit.AbilityKit.*
import kit.TestKit.*

let delegator = AbilityDelegatorRegistry.getAbilityDelegator()
let msg = "msg"
delegator.print(msg)
```

### func removeAbilityMonitor(AbilityMonitor)

```cangjie
public func removeAbilityMonitor(monitor: AbilityMonitor): Unit
```

**Description:** Removes an added [AbilityMonitor](#class-abilitymonitor) object.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Parameters:**

| Name | Type | Mandatory | Default Value | Description |
| :--- | :--- | :--- | :--- | :--- |
| monitor | [AbilityMonitor](#class-abilitymonitor) | Yes | - | [AbilityMonitor](#class-abilitymonitor) instance. |

**Exceptions:**

For detailed error codes, refer to [Ability Subsystem Error Codes](../AbilityKit/cj-errorcode-ability.md).

  | Error Code ID | Error Message |
  | :--- | :--- |
  | 16000100 | RemoveAbilityMonitor failed. |

**Example:**

<!-- compile -->

```cangjie
// index.cj

import kit.AbilityKit.*
import kit.TestKit.*

let delegator = AbilityDelegatorRegistry.getAbilityDelegator()
let monitor = AbilityMonitor(
    "EntryAbility", moduleName: "entry",
    onAbilityCreate: {ability => delegator.print("onAbilityCreate called, abilityName: ${ability.launchWant.abilityName}")}
)
delegator.removeAbilityMonitor(monitor)
```

### func removeAbilityStageMonitor(AbilityStageMonitor)

```cangjie
public func removeAbilityStageMonitor(monitor: AbilityStageMonitor): Unit
```

**Description:** Removes an added [AbilityStageMonitor](#class-abilitystagemonitor) object.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Parameters:**

| Name | Type | Mandatory | Default Value | Description |
| :--- | :--- | :--- | :--- | :--- |
| monitor | [AbilityStageMonitor](#class-abilitystagemonitor) | Yes | - | [AbilityStageMonitor](#class-abilitystagemonitor) instance. |

**Exceptions:**

For detailed error codes, refer to [Ability Subsystem Error Codes](../AbilityKit/cj-errorcode-ability.md).

  | Error Code ID | Error Message |
  | :--- | :--- |
  | 16000100 | RemoveAbilityStageMonitor failed. |

**Example:**

<!-- compile -->

```cangjie
// index.cj

import kit.AbilityKit.*
import kit.TestKit.*

let delegator = AbilityDelegatorRegistry.getAbilityDelegator()
let monitor = AbilityStageMonitor("entry", "ohos_app_cangjie_entry.MyAbilityStage")
delegator.removeAbilityStageMonitor(monitor)
```

### func startAbility(Want)

```cangjie
public func startAbility(want: Want): Unit
```

**Description:** Starts the specified [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability).

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Parameters:**

| Name | Type | Mandatory | Default Value | Description |
| :--- | :--- | :--- | :--- | :--- |
| want | [Want](../AbilityKit/cj-apis-app-ability-want.md#class-want) | Yes | - | Parameters for starting the [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability). |

**Example:**

<!-- compile -->

```cangjie
// index.cj

import kit.AbilityKit.*
import kit.TestKit.*

let delegator = AbilityDelegatorRegistry.getAbilityDelegator()
let want = Want(bundleName: "com.example.myapplication", abilityName: "EntryAbility")
delegator.startAbility(want)
```

### func waitAbilityMonitor(AbilityMonitor, Int64)

```cangjie
public func waitAbilityMonitor(monitor: AbilityMonitor, timeout!: Int64 = 5000): UIAbility
```

**Description:** Sets the wait time and waits for the [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) matching the [AbilityMonitor](#class-abilitymonitor) instance to reach the [onCreate](../AbilityKit/cj-apis-app-ability-ui_ability.md#func-oncreatewant-launchparam) lifecycle, then returns the [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) instance.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Parameters:**

| Name | Type | Mandatory | Default Value | Description |
| :--- | :--- | :--- | :--- | :--- |
| monitor | [AbilityMonitor](#class-abilitymonitor) | Yes | - | [Ability```markdown
## class AbilityDelegatorArgs

```cangjie
public class AbilityDelegatorArgs {}
```

**Description:** Test parameter information.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### prop bundleName

```cangjie
public mut prop bundleName: String
```

**Description:** Package name of the current application under test.

**Type:** String

**Access:** Read-Write

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### prop parameters

```cangjie
public mut prop parameters: HashMap<String,String>
```

**Description:** Parameters for launching the current unit test.

**Type:** HashMap\<String,String>

**Access:** Read-Write

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### prop testCaseNames

```cangjie
public mut prop testCaseNames: String
```

**Description:** Test case names.

**Type:** String

**Access:** Read-Write

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### prop testRunnerClassName

```cangjie
public mut prop testRunnerClassName: String
```

**Description:** Name of the test runner that executes the test cases.

**Type:** String

**Access:** Read-Write

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

## class AbilityDelegatorRegistry

```cangjie
public class AbilityDelegatorRegistry {}
```

**Description:** [AbilityDelegatorRegistry](#class-abilitydelegatorregistry) provides the capability of a global registry for storing registered [AbilityDelegator](#class-abilitydelegator) and [AbilityDelegatorArgs](#class-abilitydelegatorargs) objects.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### static func getAbilityDelegator()

```cangjie
public static func getAbilityDelegator(): AbilityDelegator
```

**Description:** Obtains the [AbilityDelegator](#class-abilitydelegator) object of the application, which can be used to dispatch test framework-related functionalities.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Return Value:**

|Type|Description|
|:----|:----|
|[AbilityDelegator](#class-abilitydelegator)|The [AbilityDelegator](#class-abilitydelegator) object, which can be used to dispatch test framework-related functionalities.|

### static func getArguments()

```cangjie
public static func getArguments(): AbilityDelegatorArgs
```

**Description:** Obtains the unit test parameter [AbilityDelegatorArgs](#class-abilitydelegatorargs) object.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Return Value:**

|Type|Description|
|:----|:----|
|[AbilityDelegatorArgs](#class-abilitydelegatorargs)|The [AbilityDelegatorArgs](#class-abilitydelegatorargs) object, which can be used to obtain test parameters.|

**Example:**

<!-- compile -->

```cangjie
// index.cj

import kit.TestKit.*
import kit.PerformanceAnalysisKit.*

let args = AbilityDelegatorRegistry.getArguments()
Hilog.info(0, "test", "args is ${args.bundleName}")
Hilog.info(0, "test", "args is ${args.testCaseNames}")
Hilog.info(0, "test", "args is ${args.testRunnerClassName}")
Hilog.info(0, "test", "args is ${args.parameters}")
```

## class AbilityMonitor

```cangjie
public class AbilityMonitor {
    public var abilityName: String
    public var moduleName: String
    public var onAbilityCreate:?(UIAbility) -> Unit
    public var onAbilityForeground:?(UIAbility) -> Unit
    public var onAbilityBackground:?(UIAbility) -> Unit
    public var onAbilityDestroy:?(UIAbility) -> Unit
    public var onWindowStageCreate:?(UIAbility) -> Unit
    public var onWindowStageRestore:?(UIAbility) -> Unit
    public var onWindowStageDestroy:?(UIAbility) -> Unit
    public init(
        abilityName: String,
        moduleName!: String = "",
        onAbilityCreate!: ?(UIAbility) -> Unit = None,
        onAbilityForeground!: ?(UIAbility) -> Unit = None,
        onAbilityBackground!: ?(UIAbility) -> Unit = None,
        onAbilityDestroy!: ?(UIAbility) -> Unit = None,
        onWindowStageCreate!: ?(UIAbility) -> Unit = None,
        onWindowStageRestore!: ?(UIAbility) -> Unit = None,
        onWindowStageDestroy!: ?(UIAbility) -> Unit = None
    )
}
```

**Description:** The [AbilityMonitor](#class-abilitymonitor) module provides the capability to match ability objects that meet specified conditions. The most recently matched ability object will be stored in [AbilityMonitor](#class-abilitymonitor).

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### var abilityName

```cangjie
public var abilityName: String
```

**Description:** Name of the ability bound to the current [AbilityMonitor](#class-abilitymonitor).

**Type:** String

**Access:** Read-Write

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### var moduleName

```cangjie
public var moduleName: String
```

**Description:** Name of the module bound to the current [AbilityMonitor](#class-abilitymonitor).

**Type:** String

**Access:** Read-Write

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### var onAbilityBackground

```cangjie
public var onAbilityBackground:?(UIAbility) -> Unit
```

**Description:** Callback function when the ability state changes to background. If this property is not set, the lifecycle callback will not be received.

**Type:** ?([UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability))->Unit

**Access:** Read-Write

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### var onAbilityCreate

```cangjie
public var onAbilityCreate:?(UIAbility) -> Unit
```

**Description:** Callback function when the ability is initialized. If this property is not set, the lifecycle callback will not be received.

**Type:** ?([UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability))->Unit

**Access:** Read-Write

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### var onAbilityDestroy

```cangjie
public var onAbilityDestroy:?(UIAbility) -> Unit
```

**Description:** Callback function before the ability is destroyed. If this property is not set, the lifecycle callback will not be received.

**Type:** ?([UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability))->Unit

**Access:** Read-Write

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### var onAbilityForeground

```cangjie
public var onAbilityForeground:?(UIAbility) -> Unit
```

**Description:** Callback function when the ability state changes to foreground. If this property is not set, the lifecycle callback will not be received.

**Type:** ?([UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability))->Unit

**Access:** Read-Write

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### var onWindowStageCreate

```cangjie
public var onWindowStageCreate:?(UIAbility) -> Unit
```

**Description:** Callback function when the window stage is created. If this property is not set, the lifecycle callback will not be received.

**Type:** ?([UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability))->Unit

**Access:** Read-Write

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### var onWindowStageDestroy

```cangjie
public var onWindowStageDestroy:?(UIAbility) -> Unit
```

**Description:** Callback function before the window stage is destroyed. If this property is not set, the lifecycle callback will not be received.

**Type:** ?([UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability))->Unit

**Access:** Read-Write

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### var onWindowStageRestore

```cangjie
public var onWindowStageRestore:?(UIAbility) -> Unit
```

**Description:** Callback function when the window stage is restored. If this property is not set, the lifecycle callback will not be received.

**Type:** ?([UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability))->Unit

**Access:** Read-Write

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### init(String, String, ?(UIAbility) -> Unit, ?(UIAbility) -> Unit, ?(UIAbility) -> Unit, ?(UIAbility) -> Unit, ?(UIAbility) -> Unit, ?(UIAbility) -> Unit, ?(UIAbility) -> Unit)

```cangjie
public init(
    abilityName: String,
    moduleName!: String = "",
    onAbilityCreate!: ?(UIAbility) -> Unit = None,
    onAbilityForeground!: ?(UIAbility) -> Unit = None,
    onAbilityBackground!: ?(UIAbility) -> Unit = None,
    onAbilityDestroy!: ?(UIAbility) -> Unit = None,
    onWindowStageCreate!: ?(UIAbility) -> Unit = None,
    onWindowStageRestore!: ?(UIAbility) -> Unit = None,
    onWindowStageDestroy!: ?(UIAbility) -> Unit = None
)
```

**Description:** Constructs an [AbilityMonitor](#class-abilitymonitor) object.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Parameters:**

|Parameter|Type|Required|Default|Description|
|:---|:---|:---|:---|:---|
|abilityName|String|Yes|-|Name of the ability bound to the current [AbilityMonitor](#class-abilitymonitor).|
|moduleName|String|No|""| **Named parameter.** Name of the module bound to the current [AbilityMonitor](#class-abilitymonitor).|
|onAbilityCreate|?([UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability)) -> Unit|No|None| **Named parameter.** Callback function when the ability is initialized. None means this property is not set, and the lifecycle callback will not be received.|
|onAbilityForeground|?([UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability)) -> Unit|No|None| **Named parameter.** Callback function when the ability state changes to foreground. None means this property is not set, and the lifecycle callback will not be received.|
|onAbilityBackground|?([UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability)) -> Unit|No|None| **Named parameter.** Callback function when the ability state changes to background. None means this property is not set, and the lifecycle callback will not be received.|
|onAbilityDestroy|?([UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability)) -> Unit|No|None| **Named parameter.** Callback function before the ability is destroyed. None means this property is not set, and the lifecycle callback will not be received.|
|onWindowStageCreate|?([UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability)) -> Unit|No|None| **Named parameter.** Callback function when the window stage is created. None means this property is not set, and the lifecycle callback will not be received.|
|onWindowStageRestore|?([UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability)) -> Unit|No|None| **Named parameter.** Callback function when the window stage is restored. None means this property is not set, and the lifecycle callback will not be received.|
|onWindowStageDestroy|?([UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability)) -> Unit|No|None| **Named parameter.** Callback function before the window stage is destroyed. None means this property is not set, and the lifecycle callback will not be received.|

**Example:**

<!-- compile -->

```cangjie
// index.cj

import kit.TestKit.*

let delegator = AbilityDelegatorRegistry.getAbilityDelegator()
let monitor = AbilityMonitor(
    "EntryAbility", moduleName: "entry",
    onAbilityCreate: {ability => delegator.print("onAbilityCreate called, abilityName: ${ability.launchWant.abilityName}")}
)
```

## class AbilityStageMonitor

```cangjie
public class AbilityStageMonitor <: FFIData {
    public var moduleName: String
    public var srcEntrance: String
    public init(
        moduleName: String,
        srcEntrance: String
    )
}
```

**Description:** The [AbilityStageMonitor](#class-abilitystagemonitor) module provides the capability to match [AbilityStage](../AbilityKit/cj-apis-app-ability-ability_stage.md#class-abilitystage) objects that meet specified conditions. The most recently matched [AbilityStage](../AbilityKit/cj-apis-app-ability-ability_stage.md#class-abilitystage) object will be stored in [AbilityStageMonitor](#class-abilitystagemonitor).

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Parent Type:**

- FFIData

### var moduleName

```cangjie
public var moduleName: String
```

**Description:** Module name of the abilityStage to be monitored.

**Type:** String

**Access:** Read-Write

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### var srcEntrance

```cangjie
public var srcEntrance: String
```

**Description:** Source path of the abilityStage to be monitored.

**Type:** String

**Access:** Read-Write

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### init(String, String)

```cangjie
public init(
    moduleName: String,
    srcEntrance: String
)
```

**Description:** Constructs an [AbilityStageMonitor](#class-abilitystagemonitor) object.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Parameters:**

|Parameter|Type|Required|Default|Description|
|:---|:---|:---|:---|:---|
|moduleName|String|Yes|-|Module name of the abilityStage to be monitored.|
|srcEntrance|String|Yes|-|Source path of the abilityStage to be monitored.|

**Example:**

<!-- compile -->

```cangjie
// index.cj

import kit.AbilityKit.*
import kit.TestKit.*

let delegator = AbilityDelegatorRegistry.getAbilityDelegator()
let monitor = AbilityStageMonitor("entry", "ohos_app_cangjie_entry.MyAbilityStage")
delegator.addAbilityStageMonitor(monitor)
```## class ShellCmdResult

```cangjie
public class ShellCmdResult {}
```

**Description:** Shell command execution result.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### prop exitCode

```cangjie
public mut prop exitCode: Int32
```

**Description:** Result code.

**Type:** Int32

**Access:** Read-write

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### prop stdResult

```cangjie
public mut prop stdResult: String
```

**Description:** Standard output content.

**Type:** String

**Access:** Read-write

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

## enum AbilityLifecycleState

```cangjie
public enum AbilityLifecycleState <: Equatable<AbilityLifecycleState> & ToString {
    | Uninitialized
    | Create
    | Foreground
    | Background
    | Destroy
    | ...
}
```

**Description:** [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) lifecycle state. This enumeration type can be used with the [getAbilityState](#func-getabilitystateuiability) method of [AbilityDelegator](#class-abilitydelegator) to return different ability lifecycle states.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

**Parent Types:**

- Equatable\<AbilityLifecycleState>
- ToString

### Background

```cangjie
Background
```

**Description:** Indicates the [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) is in background state.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### Create

```cangjie
Create
```

**Description:** Indicates the [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) is in created state.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### Destroy

```cangjie
Destroy
```

**Description:** Indicates the [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) is in destroyed state.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### Foreground

```cangjie
Foreground
```

**Description:** Indicates the [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) is in foreground state.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### Uninitialized

```cangjie
Uninitialized
```

**Description:** Indicates the [UIAbility](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) is in invalid state.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 22

### func !=(AbilityLifecycleState)

```cangjie
public operator func !=(other: AbilityLifecycleState): Bool
```

**Description:** Determines whether two enumeration values are unequal.

**Parameters:**

| Name | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| other | [AbilityLifecycleState](#enum-abilitylifecyclestate) | Yes | - | Another enumeration value. |

**Return Value:**

| Type | Description |
|:----|:----|
| Bool | Returns true if the two enumeration values are unequal, otherwise returns false. |

### func ==(AbilityLifecycleState)

```cangjie
public operator func ==(other: AbilityLifecycleState): Bool
```

**Description:** Determines whether two enumeration values are equal.

**Parameters:**

| Name | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| other | [AbilityLifecycleState](#enum-abilitylifecyclestate) | Yes | - | Another enumeration value. |

**Return Value:**

| Type | Description |
|:----|:----|
| Bool | Returns true if the two enumeration values are equal, otherwise returns false. |

### func toString()

```cangjie
public func toString(): String
```

**Description:** Gets the string representation of the current enumeration.

**Return Value:**

| Type | Description |
|:----|:----|
| String | String representation of the current enumeration. |