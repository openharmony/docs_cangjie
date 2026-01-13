# Environment: Device Environment Query

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

Developers who need to access the environmental parameters of the device running the application to make different scenario judgments—such as multilingual support or light/dark mode—should utilize the Environment device environment query.

Environment is a singleton object created by the ArkUI framework when the application starts. It provides a series of properties describing the application's runtime state to [AppStorage](./cj-appstorage.md). All properties of Environment are immutable (i.e., applications cannot write to them), and all properties are of simple types.

Environment offers the capability to read certain system environment variables (see [Environment Built-in Parameters](#environment-built-in-parameters)) and writes their values into AppStorage. Therefore, developers must access AppStorage to obtain the values of these environment variables.

Before reading this documentation, it is recommended to review: [AppStorage](./cj-appstorage.md).

## Environment Built-in Parameters

| Key | Data Type | Description |
|:---|:---|:---|
| accessibilityEnabled | Bool | Indicates whether screen reader accessibility is enabled. |
| colorMode | [ColorMode](../../reference/arkui-cj/cj-state-rendering-appstatemanagement.md#enum-colormode) | Color scheme type: options are ColorMode.Light (light mode) and ColorMode.Dark (dark mode). |
| fontScale | Float64 | Font size scaling factor. Developers must configure `fontSizeScale` as "followSystem" in the `configuration`. For configuration steps, refer to [configuration](../../cj-start/basic-knowledge/app-configuration-file.md#configuration-tag) to ensure `fontScale` follows system changes.<br>Initial value aligns with the system default. |
| fontWeightScale | Float64 | Font weight scaling factor. The range of `fontWeightScale` may vary across systems or device models.<br>Initial value aligns with the system default. |
| layoutDirection | [LayoutDirection](../../reference/arkui-cj/cj-state-rendering-appstatemanagement.md#enum-layoutdirection) | Layout direction type: includes LayoutDirection.Ltr (left-to-right) and LayoutDirection.Rtl (right-to-left). |
| languageCode | String | Current system language code, which must be in lowercase letters (e.g., "zh").<br>Initial value aligns with the system default. |

## Usage Scenarios

### Accessing Environment Parameters from UI

- Use `Environment.[envProp](../../reference/arkui-cj/cj-state-rendering-appstatemanagement.md#static-func-envproptstring-t)` to store device environment variables in AppStorage.

    ```cangjie
    // Store the device's language code in AppStorage with a default value of "en"
    Environment.envProp<String>("languageCode", "en")
    ```

- Retrieve the `languageCode` value in a custom component via `@StorageProp`.

    ```cangjie
    @StorageProp["languageCode"] let languageCode: String = "en"
    ```

The update chain from device environment to Component is: Environment --> AppStorage --> Component.

> **Note:**
>
> Environment parameters associated with `@StorageProp` can be modified locally but cannot be synchronized back to AppStorage because environment variables are read-only in the application and can only be queried via Environment.

 <!-- run -->

```cangjie
package ohos_app_cangjie_entry
import kit.ArkUI.*
import ohos.arkui.state_macro_manage.*

@Entry
@Component
class EntryView {
    let SysLanguageCode = Environment.envProp<String>("languageCode", "en")
    @StorageProp["languageCode"]
    let languageCode: String = "en"
    func build() {
        Row() {
            Column() {
                // Display the current device's languageCode
                Text(this.languageCode)
            }
        }
    }
}
```

### Using Environment in Application Logic

 <!-- run -->

```cangjie
package ohos_app_cangjie_entry
import kit.ArkUI.*
import ohos.arkui.state_macro_manage.*
import kit.PerformanceAnalysisKit.Hilog

@Entry
@Component
class EntryView {
    // Store the device's languageCode in AppStorage using Environment.EnvProp
    let SysLanguageCode = Environment.envProp<String>("languageCode", "en")
    // Retrieve the unidirectionally bound languageCode variable from AppStorage
    let lang: ObservedProperty<String> = AppStorage.`prop`<String>('languageCode').getOrThrow()
    func build() {
        Row() {
            Column() {
                Button("lang")
                .onClick({
                    evt =>
                        if (lang.get()=='zh') {
                            Hilog.info(0, "Chinese", "Hello")
                        } else {
                            Hilog.info(0, "En", "Hello")
                        }
                })
            }
        }
    }
}
```