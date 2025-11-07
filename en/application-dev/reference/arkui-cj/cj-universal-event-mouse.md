# Mouse Events

When a single action triggers multiple events, the order of events is fixed, and mouse events are passed through by default.

> Note:
>
> Currently, only triggering via an external mouse is supported.

## Import Module

```cangjie
import kit.ArkUI.*
```

## func onMouse(?(MouseEvent) -> Unit)

```cangjie
func onMouse(event: ?(MouseEvent) -> Unit): T
```

**Function:** Triggers when the current component is clicked by a mouse button or when the mouse moves over the component.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| event | ?([MouseEvent](./cj-common-types.md#class-mouseevent)) -> Unit | Yes | - | Callback triggered when the component is clicked by a mouse button or when the mouse moves over the component. The MouseEvent parameter includes the timestamp when the event was triggered, the mouse button, the action, the coordinates of the click point on the entire screen, and the coordinates of the click point relative to the current component.<br>Initial value: { _: MouseEvent => }. |

**Return Value:**

| Type | Description |
| :--- | :--- |
| T | Returns the generic method interface type. |