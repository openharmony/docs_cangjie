# Making Phone Calls

## Scenario Description

Developers can implement phone call functionality through the following methods:

- For third-party applications, developers can use the `makeCall` interface to launch the system phone app, allowing users to initiate calls themselves.

## Basic Concepts

- Call Status Codes  
  Reports the current call status to the app, enabling logical processing based on the current call state. For example, when there is no ongoing call, a new call can be initiated normally.

| Name                | Description                               |
| :------------------ | :--------------------------------- |
| CALL_STATE_UNKNOWN | Invalid state, returned when call status retrieval fails.   |
| CALL_STATE_IDLE    | Indicates no ongoing calls.              |
| CALL_STATE_RINGING | Indicates an incoming call is ringing or on hold.              |
| CALL_STATE_OFFHOOK | Indicates at least one call is in dialing, active, or hold state, with no new incoming calls ringing or on hold. |

## Constraints and Limitations

1. Only supported on standard systems.
2. The device must have an active SIM card inserted.

## Interface Description

> **Note:**  
>
> To ensure application efficiency, most API calls are asynchronous. For asynchronous APIs, both callback and Promise approaches are provided. The following examples use callback functions.

| Interface Name | Description |
| :------------------------------------------- | :--------------------------------- |
| hasVoiceCapability() | Checks whether voice capability is supported. |
| makeCall(UIAbilityContext, String) | Redirects to the dial screen and displays the callee number.  |

## Development Procedure

Example of using `makeCall` to make a phone call:

1. Import the `call` and `observer` modules.
2. Call `hasVoiceCapability` to confirm whether the current device supports dialing.
3. Call the `makeCall` interface to navigate to the dial screen and display the number to be dialed.

<!-- compile -->

```cangjie
// Import required modules
import kit.TelephonyKit.*
import kit.AbilityKit.*

var ctx = Option<UIAbilityContext>.None

@Entry
@Component
class EntryView {
    @State
    var message: String = "Hello World"

    func build() {
        Row {
            Column {
                Text(this.message)
                    .fontSize(50)
                    .fontWeight(FontWeight.Bold)
                    .onClick {
                        evt =>
                        let isSupport = Call.hasVoiceCapability()
                        if (isSupport) {
                            // If the device supports call capability, proceed to the dial screen and display the number to be dialed
                            Call.makeCall(ctx.getOrThrow(), "130xxxx")                  
                        }
                    }
            }.width(100.percent)
        }.height(100.percent)
    }
}
```

<!-- compile -->

```cangjie
// main_ability.cj
import ohos.ability.AbilityStage
import ohos.ability.LaunchReason

class MainAbility <: UIAbility {
    public init() {
        super()
        registerSelf()
    }

    public override func onCreate(want: Want, launchParam: LaunchParam): Unit {
        Hilog.info(1, "info", "MainAbility OnCreated.${want.abilityName}")
        match (launchParam.launchReason) {
            case LaunchReason.START_ABILITY => Hilog.info(1, "info", "START_ABILITY")
            case _ => ()
        }
    }

    public override func onWindowStageCreate(windowStage: WindowStage): Unit {
        Hilog.info(1, "info", "MainAbility onWindowStageCreate.")
        windowStage.loadContent("EntryView")
        // declared in index.cj
        ctx = this.context
    }
}
```