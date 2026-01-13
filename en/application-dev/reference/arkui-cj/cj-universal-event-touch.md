# Touch Event

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

Triggered when a finger presses, slides, or lifts on a component.

## Import Module

```cangjie
import kit.ArkUI.*
```

## func onTouch(?(TouchEvent) -> Unit)

```cangjie
func onTouch(event: ?(TouchEvent) -> Unit): T
```

**Function:** Triggered by finger touch actions.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| event | ?([TouchEvent](./cj-common-types.md#class-touchevent)) -> Unit | Yes | - | Callback function triggered by finger touch actions.<br>Initial value: { _: TouchEvent => }. |

**Return Value:**

| Type | Description |
|:---|:---|
| T | Returns the generic method interface type |