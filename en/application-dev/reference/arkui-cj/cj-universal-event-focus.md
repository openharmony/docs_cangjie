# Focus Events

Focus events are triggered when the page focus moves between focusable components. Components can use focus events to handle related logic.

> **Note:**
>
> - Currently, only triggering via the Tab key or arrow keys on an external keyboard is supported. Keyboard navigation focus movement is not supported in nested scrolling component scenarios.
> - Components with default interaction logic, such as [Button](./cj-button-picker-button.md) and [TextInput](./cj-text-input-textinput.md), are focusable by default. Components like [Text](./cj-text-input-text.md) and [Image](./cj-image-video-image.md) are non-focusable by default. In a non-focusable state, focus events cannot be triggered. The `focusable` attribute must be set to `true` to enable triggering.
> - For container components with focus capability, such as [Stack](./cj-row-column-stack-stack.md) and [Row](./cj-row-column-stack-row.md), if they contain no focusable child components, the container itself cannot receive focus. Configuring `onClick` or a single-finger tap gesture for such components will implicitly make them focusable.
> - For focus development and component focus capability, refer to the [Focus Development Guide](../../arkui-cj/cj-common-events-focus-event.md).

## Import Module

```cangjie
import kit.ArkUI.*
```

## func onFocus(?() -> Unit)

```cangjie
func onFocus(event: ?() -> Unit): T
```

**Function:** Triggered when the current component gains focus.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| event | ?() -> Unit | Yes | - | Callback function triggered when the current component gains focus. |

**Return Value:**

| Type | Description |
|:---|:---|
| T | Returns the generic method interface type. |


## func onBlur(?() -> Unit)

```cangjie
func onBlur(event: ?() -> Unit): T
```

**Function:** Triggered when the current component loses focus.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| event | ?() -> Unit | Yes | - | Callback function triggered when the current component loses focus. |

**Return Value:**

| Type | Description |
|:---|:---|
| T | Returns the generic method interface type. |