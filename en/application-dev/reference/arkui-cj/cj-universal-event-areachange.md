# Component Area Change Event

The component area change event refers to an event triggered when the displayed size, position, or other attributes of a component change.

> **Note:**
>
> The execution of the `onAreaChange` callback is only related to the component itself. There is no strict execution order or guarantee for the callbacks of `onAreaChange` on ancestor or descendant components.

## Import Module

```cangjie
import kit.ArkUI.*
```

## func onAreaChange(?(Area, Area) -> Unit)

```cangjie
func onAreaChange(event: ?(Area, Area) -> Unit): T
```

**Function:** This callback is triggered when the component's area changes. It only responds to callbacks caused by layout changes that affect the component's size or position.

Changes in rendering attributes due to drawing operations (e.g., `translate`, `offset`) will not trigger this callback. If the component's position is determined by drawing changes (e.g., `bindSheet`), it will also not trigger the callback.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since Version:** 22

**Parameters:**

| Parameter | Type | Required | Default Value | Description |
|:---|:---|:---|:---|:---|
| event | ?([Area](./cj-common-types.md#class-area), [Area](./cj-common-types.md#class-area)) -> Unit | Yes | - | Callback triggered when the component's area changes.<br/>Parameter 1: Component area information before the change.<br/>Parameter 2: Component area information after the change. |

**Return Value:**

| Type | Description |
|:---|:---|
| T | Returns the generic method interface type |