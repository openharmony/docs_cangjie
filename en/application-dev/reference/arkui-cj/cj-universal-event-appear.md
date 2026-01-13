# Mounting and Unmounting Events

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

Mounting and unmounting events refer to the events triggered when a component is mounted to or unmounted from the component tree.

## Import Module

```cangjie
import kit.ArkUI.*
```

## func onAppear(?() -> Unit)

```cangjie
func onAppear(event: ?() -> Unit): T
```

**Function:** This callback is triggered when the component is mounted and displayed.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default Value | Description |
|:---|:---|:---|:---|:---|
| event | ?() -> Unit | Yes | - | Callback function triggered when the component is mounted and displayed. The callback may be invoked after the component's layout rendering is completed. |

**Return Value:**

| Type | Description |
|:---|:---|
| T | Returns the generic method interface type |

## func onDisAppear(?() -> Unit)

```cangjie
func onDisAppear(event: ?() -> Unit): T
```

**Function:** This callback is triggered when the component is unmounted and disappears.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default Value | Description |
|:---|:---|:---|:---|:---|
| event | ?() -> Unit | Yes | - | Callback function triggered when the component is unmounted and disappears. The callback may be invoked after the component's layout rendering is completed. |

**Return Value:**

| Type | Description |
|:---|:---|
| T | Returns the generic method interface type |