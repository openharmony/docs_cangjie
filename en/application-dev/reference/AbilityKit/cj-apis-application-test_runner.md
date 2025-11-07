# ohos.application.test_runner

This module provides framework testing capabilities.

## Importing the Module

```cangjie
import kit.AbilityKit.*
```

## Permission List

ohos.permission.DISTRIBUTED_DATASYNC

ohos.permission.PREPARE_APP_TERMINATE

ohos.permission.PRIVACY_WINDOW

## Usage Instructions

API sample code usage instructions:

- If the sample code has a "// index.cj" comment in the first line, it indicates the example can be compiled and run in the "index.cj" file of a Cangjie template project.
- If the sample requires obtaining the [Context](./cj-apis-app-ability-ui_ability.md#class-context) application context, it needs to be configured in the "main_ability.cj" file of the Cangjie template project.

For details about the sample project and configuration template mentioned above, refer to [Cangjie Sample Code Instructions](../cj-development-intro.md#Cangjie-Sample-Code-Instructions).

## class TestRunner

```cangjie
public open class TestRunner {}
```

**Functionality:** Provides framework testing capabilities.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** Version 22

### static func registerCreator(String, () -> TestRunner)

```cangjie
public static func registerCreator(name: String, creator: () -> TestRunner): Unit
```

**Functionality:** Registers a function for creating [TestRunner](#class-testrunner) objects.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** Version 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| name | String | Yes | - | Identifier for the constructor function. |
| creator | ()->[TestRunner](#class-testrunner) | Yes | - | Function for creating [TestRunner](#class-testrunner) objects. |

**Example:**

<!-- compile -->
```cangjie
import kit.TestKit.*

let TESTRUNNER_REGISTER_RESULT = TestRunner.registerCreator("test", () -> MyTestRunner)

class MyTestRunner <: TestRunner {
    public override func onPrepare(): Unit {
    }
}
```

### func onPrepare()

```cangjie
public open func onPrepare(): Unit
```

**Functionality:** Executes test cases.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** Version 22

**Example:**

<!-- compile -->
```cangjie
import kit.TestKit.*

let TESTRUNNER_REGISTER_RESULT = TestRunner.registerCreator("test", () -> MyTestRunner)

class MyTestRunner <: TestRunner {
    public override func onPrepare(): Unit {
    }
}
```

### func onRun()

```cangjie
public open func onRun(): Unit
```

**Functionality:** Prepares the unit testing environment for executing test cases.

**System Capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** Version 22

**Example:**

<!-- compile -->
```cangjie
import kit.TestKit.*

let TESTRUNNER_REGISTER_RESULT = TestRunner.registerCreator("test", () -> MyTestRunner)

class MyTestRunner <: TestRunner {
    public override func onRun(): Unit {
    }
}
```