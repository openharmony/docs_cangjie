# UIAbility Component Lifecycle

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

## Overview

When users open, switch, or return to an application, the [UIAbility](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) instances within the application transition between different states in their lifecycle. The UIAbility class provides a series of callbacks that notify when the current UIAbility instance undergoes state changes, including creation and destruction, or transitions between foreground and background states.

The UIAbility lifecycle consists of four states: Create, Foreground, Background, and Destroy, as illustrated below.

**Figure 1** UIAbility Lifecycle States

![Ability-Life-Cycle](figures/Ability-Life-Cycle.png)<!-- ToBeReviewd -->

## Lifecycle State Descriptions

### Create State

The Create state is triggered when a [UIAbility](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) instance is created during the application loading process. The system invokes the [onCreate()](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#func-oncreatewant-launchparam) callback. This callback can be used for page initialization tasks, such as variable definition and resource loading, to prepare for subsequent UI rendering.

<!-- compile -->

```cangjie
internal import kit.AbilityKit.UIAbility
internal import kit.AbilityKit.Want

class MainAbility <: UIAbility {
    public override func onCreate(want: Want, launchParam: LaunchParam): Unit {
      // Page initialization
    }
    // ...
}
```

> **Note:**
>
> [Want](../reference/AbilityKit/cj-apis-app-ability-want.md#class-want) serves as a carrier for information transfer between objects and can be used for inter-component communication within applications. For detailed information about Want, refer to [Information Carrier Want](cj-want-overview.md).

### WindowStageCreate and WindowStageDestroy States

After a [UIAbility](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) instance is created and before it enters the Foreground state, the system creates a WindowStage. Upon completion, the [onWindowStageCreate()](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#func-onwindowstagecreatewindowstage) callback is triggered. This callback can be used to configure UI loading and set up event subscriptions for the WindowStage.

**Figure 2** WindowStageCreate and WindowStageDestroy States

![Ability-Life-Cycle-WindowStage](figures/Ability-Life-Cycle-WindowStage.png)<!-- ToBeReviewd -->

Within the onWindowStageCreate() callback, use the [loadContent()](../reference/arkui-cj/cj-apis-window.md#class-windowstage) method to specify the page to be loaded by the application. Additionally, subscribe to [WindowStage events](../reference/arkui-cj/cj-apis-window.md#enum-windowstageeventtype) (focus/unfocus, foreground/background transitions, interactive/non-interactive states) by calling the [on('windowStageEvent')](../reference/arkui-cj/cj-apis-window.md#func-onwindowcallbacktype-callback1argumentwindowstageeventtype) method as needed.

> **Note:**
>
> The timing of [WindowStage events](../reference/arkui-cj/cj-apis-window.md#enum-windowstageeventtype) may vary across different development scenarios.

<!-- compile -->

```cangjie
import kit.AbilityKit.UIAbilityContext
import kit.AbilityKit.UIAbility
import kit.ArkUI.{WindowStage, WindowCallbackType, WindowStageEventType}
import ohos.callback_invoke.Callback1Argument
import ohos.business_exception.BusinessException

class WindowStageCallback <: Callback1Argument<WindowStageEventType> {
    public override func invoke(err: ?BusinessException, arg: WindowStageEventType) {
        match (arg) {
            case WindowStageEventType.Shown => // Transition to foreground
                Hilog.info(1, "info", "windowStage foreground.")
            case WindowStageEventType.Active => // Focus state
                Hilog.info(1, "info", "windowStage active.")
            case WindowStageEventType.Inactive => // Unfocus state
                Hilog.info(1, "info", "windowStage inactive.")
            case WindowStageEventType.Hidden => // Transition to background
                Hilog.info(1, "info", "windowStage background.")
            case WindowStageEventType.Resumed => // Interactive state
                Hilog.info(1, "info", "windowStage resumed.")
            case WindowStageEventType.Paused => // Non-interactive state
                Hilog.info(1, "info", "windowStage paused.")
            case _ => ()
        }
    }
}

class MainAbility <: UIAbility {
    // ...
    public override func onWindowStageCreate(windowStage: WindowStage): Unit {
        // Subscribe to WindowStage events (focus/unfocus, foreground/background transitions, interactive/non-interactive states)
        try {
            windowStage.on(WindowStageEvent, WindowStageCallback())
        } catch (e: BusinessException) {
            AppLog.error("Failed to enable the listener for window stage event changes. Cause: ${e.message}");
        }
        // Configure UI loading
        windowStage.loadContent("EntryView")
    }
}
```

> **Note:**
>
> For guidance on using WindowStage, refer to [Window Development Guide](../reference/arkui-cj/cj-apis-window.md).

### Foreground and Background States

The Foreground and Background states are triggered when a [UIAbility](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) instance transitions to the foreground or background, respectively, corresponding to the [onForeground()](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#func-onforeground) and [onBackground()](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#func-onbackground) callbacks.

The `onForeground()` callback is triggered before the UI of the UIAbility becomes visible, such as when transitioning to the foreground. Use this callback to request system resources or reacquire resources released during `onBackground()`.

The `onBackground()` callback is triggered after the UI of the UIAbility becomes completely invisible, such as when transitioning to the background. Use this callback to release resources unnecessary when the UI is invisible or to perform time-consuming operations like state preservation.

For example, if an application requires user location data and has obtained the necessary permissions, the location service can be activated in the `onForeground()` callback to retrieve current location information.

When the application transitions to the background, the location service can be deactivated in the `onBackground()` callback to conserve system resources.

<!-- compile -->

```cangjie
import kit.AbilityKit.UIAbility

class MainAbility <: UIAbility {
    // ...

    public override func onForeground(): Unit {
        // Request system resources or reacquire resources released in onBackground()
    }

    public override func onBackground(): Unit {
        // Release unnecessary resources or perform time-consuming operations
        // such as state preservation
    }
}
```

When a UIAbility instance is already created and configured with the [singleton](cj-uiability-launch-type.md#singleton启动模式) launch mode, invoking the [startAbility()](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#func-startabilityforresultwant-asynccallbackabilityresult) method again to launch this UIAbility instance will only trigger the [onNewWant()](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#func-onnewwantwant-launchparam) callback, bypassing the [onCreate()](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#func-oncreatewant-launchparam) and [onWindowStageCreate()](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#func-onwindowstagecreatewindowstage) lifecycle callbacks. Use this callback to update resources and data for subsequent UI rendering.

<!-- compile -->

```cangjie
import kit.AbilityKit.{UIAbility, Want, LaunchParam}

class MainAbility <: UIAbility {
    // ...
    public override func onNewWant(want: Want, launchParam: LaunchParam): Unit {
        // Update resources and data
    }
}
```

### Destroy State

The Destroy state is triggered when a [UIAbility](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) instance is destroyed. Use the onDestroy() callback to release system resources, save data, and perform other cleanup operations.

For example, calling the [terminateSelf()](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#func-terminateself) method stops the current UIAbility instance, invokes the onDestroy() callback, and completes the destruction of the UIAbility instance.

<!--RP1-->
Similarly, when a user closes the UIAbility instance via the recent tasks list, the onDestroy() callback is executed, and the UIAbility instance is destroyed.

> **Note:**
>
> When debugging an application in developer mode, removing a task of the debugged application from the recent tasks list will forcibly terminate the application's process.

<!--RP1End-->

<!-- compile -->

```cangjie
import kit.AbilityKit.UIAbility

class MainAbility <: UIAbility {
    // ...

    public override func onDestroy(): Unit {
        // Release system resources and save data
    }
}
```