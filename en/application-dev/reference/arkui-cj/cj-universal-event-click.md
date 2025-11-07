# Click Event

A click event refers to the event triggered when a component is clicked.

## Import Module

```cangjie
import kit.ArkUI.*
```

## func onClick(?(ClickEvent) -> Unit)

```cangjie
func onClick(event: ?(ClickEvent) -> Unit): T
```

**Function:** Event triggered when the component is clicked.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default Value | Description |
|:---|:---|:---|:---|:---|
| event | ?([ClickEvent](./cj-common-types.md#class-clickevent)) -> Unit | Yes | - | Callback function triggered when the component is clicked. |

**Return Value:**

| Type | Description |
|:---|:---|
| T | Returns the generic method interface type |