# Basic Usage of UIAbility Component

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

The basic usage of the [UIAbility](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) component includes: specifying the startup page for UIAbility and obtaining the context information of UIAbility [UIAbilityContext](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiabilitycontext).

## Specifying the Startup Page for UIAbility

When launching a [UIAbility](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) in an application, it is necessary to specify the startup page. Otherwise, the application may display a blank screen after launch due to the absence of a default loaded page. The startup page can be set in the [onWindowStageCreate()](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#func-onwindowstagecreatewindowstage) lifecycle callback of UIAbility by using the [loadContent()](../reference/arkui-cj/cj-apis-window.md#class-windowstage) method of the [WindowStage](../reference/arkui-cj/cj-apis-window.md#class-windowstage) object.

<!-- compile -->

```cangjie
import kit.AbilityKit.UIAbility
import kit.ArkUI.WindowStage

class MainAbility <: UIAbility {
    public override func onWindowStageCreate(windowStage: WindowStage): Unit {
        // Main window is created, set main page for this ability
        windowStage.loadContent("EntryView")
    }
    // ...
}
```

> **Note:**
>
> In DevEco Studio, the UIAbility instance created by default will load the Index page. Replace the Index page class name with the desired page class name as needed.

## Obtaining Context Information of UIAbility

The [UIAbility](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) class has its own context information, which is an instance of the [UIAbilityContext](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiabilitycontext) class. The [UIAbilityContext](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiabilitycontext) class includes properties such as abilityInfo and currentHapModuleInfo. Through AbilityContext, you can obtain relevant configuration information of the Ability, such as the package code path, Bundle name, Ability name, and environmental state required by the application. Additionally, you can access methods to operate the Ability instance (e.g., [startAbility()](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#func-startabilitywant), [terminateSelf()](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#func-terminateself)).

- In UIAbility, you can obtain the context information of the UIAbility instance via `this.context`.

  <!-- compile -->

  ```cangjie
  import kit.AbilityKit.{UIAbility, UIAbilityContext, Want, LaunchParam}
  import kit.ArkUI.WindowStage

  var globalContext : ?UIAbilityContext = None

  class MainAbility <: UIAbility {
      public override func onWindowStageCreate(windowStage: WindowStage): Unit {
          // Obtain the context of the Ability instance
          globalContext = this.context
          windowStage.loadContent("EntryView")
    }
  }
  ```

- To obtain the context information of the UIAbility instance in a page, it involves two parts: importing the dependent resource context module and defining a context variable in the component.

  <!-- compile -->

  ```cangjie
  import kit.AbilityKit.{UIAbilityContext, Want}

  func getContext(): UIAbilityContext {
      return globalContext.getOrThrow()
  }

  @Entry
  @Component
  class EntryView {
      @State
      var context: UIAbilityContext = getContext()

      func startAbilityTest(): Unit {
          let want = Want(
              // Want parameter information
          )
          context.startAbility(want)
      }

      // Page display
      func build() {
          // ...
      }
  }
  ```

  Alternatively, after importing the dependent resource context module, you can define the variable before using [UIAbilityContext](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiabilitycontext).
  
  <!-- compile -->

  ```cangjie
  import kit.AbilityKit.{UIAbilityContext, Want}

  func getContext(): UIAbilityContext {
      return globalContext.getOrThrow()
  }

  @Entry
  @Component
  class EntryView {
      func startAbilityTest(): Unit {
          let context = getContext()
          let want = Want(
              // Want parameter information
          )
          context.startAbility(want)
      }

      // Page display
      func build() {
          // ...
      }
  }
  ```

- After completing the business logic, if developers want to terminate the current [UIAbility](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) instance, they can do so by calling the [terminateSelf()](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#func-terminateself) method.

  <!-- compile -->

  ```cangjie
  internal import kit.PerformanceAnalysisKit.Hilog
  import kit.AbilityKit.{UIAbilityContext, Want}

  func getContext(): UIAbilityContext {
      return globalContext.getOrThrow()
  }

  @Entry
  @Component
  class EntryView {
      func build() {
          Row {
              Column {
                  Text("")
                      .fontSize(50)
                      .fontWeight(FontWeight.Bold)
                      .onClick ({
                          evt =>
                          let context = getContext()
                          try {
                              // Execute normal business
                              context.terminateSelf()
                          } catch (e: Exception) {
                              // Handle business logic errors
                              Hilog.error(0, "terminateSelf failed", " message is ${e.toString()}")
                          }
                      })
              }.width(100.percent)
          }.height(100.percent)
      }
  }
  ```