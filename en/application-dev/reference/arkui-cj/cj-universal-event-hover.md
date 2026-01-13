# Hover Event

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

Triggered when the cursor slides or a stylus hovers and moves over a component on the screen.

> **Note:**
>
> Currently supported triggers include external mice, styluses, and touchpads.

## Import Module

```cangjie
import kit.ArkUI.*
```

## func onHover(?(Bool) -> Unit)

```cangjie
func onHover(event: ?(Bool) -> Unit): T
```

**Function:** Triggers this event when the mouse enters or exits the component.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default Value | Description |
|:---|:---|:---|:---|:---|
| event | ?(Bool) -> Unit | Yes | - | Callback function triggered when the mouse enters or exits the component.<br>Returns `true` when the mouse enters and `false` when it exits. |

**Return Value:**

| Type | Description |
|:---|:---|
| T | Returns the generic method interface type |