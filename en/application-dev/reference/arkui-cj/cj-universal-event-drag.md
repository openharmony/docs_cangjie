# Drag Events

Drag events refer to events triggered when a component is long-pressed and dragged.

> **Note:**
>
> Pre-installed resource files of the application (i.e., resource files existing in the HAP package before installation) only support intra-application local dragging.

The ArkUI framework provides default drag capabilities for the following components, supporting drag-out or drag-in responses. Developers can also customize drag responses by implementing generic drag events.

- Components with default drag-out support (data can be dragged from these components): [Search](./cj-text-input-search.md), [TextInput](./cj-text-input-textinput.md), [TextArea](./cj-text-input-textarea.md), [RichEditor](./cj-text-input-richeditor.md), [Text](./cj-text-input-text.md), [Image](./cj-image-video-image.md). Developers can control the use of default drag capabilities by setting the `draggable` property of these components.

- Components with default drag-in support (target components can respond to dragged-in data): [Search](./cj-text-input-search.md), [TextInput](./cj-text-input-textinput.md), [TextArea](./cj-text-input-textarea.md), [RichEditor](./cj-text-input-richeditor.md). Developers can disable default drag-in support by setting the `allowDrop` property of these components to `null`.

For other components, developers need to set the `draggable` property to `true` and implement data transfer-related content in interfaces like `onDragStart` to handle dragging correctly.

> **Note:**
>
> The `Text` component must be used in conjunction with [copyOption](./cj-text-input-text.md#func-copyoptioncopyoptions), setting `copyOptions` to either `CopyOptions.InApp` or `CopyOptions.LocalDevice`.

## Import Module

```cangjie
import kit.ArkUI.*
```

## func onDragStart(?(DragInfo) -> DragItemInfo)

```cangjie
func onDragStart(event: ?(DragInfo) -> DragItemInfo): T
```

**Function:** Triggered when the component bound to this event is dragged for the first time, with a long-press duration ≥ 500ms and finger movement distance ≥ 10vp.

For components with default drag-out support, if the developer sets `onDragStart`, the developer's `onDragStart` is executed first, and the system's default drag-out capability is determined based on the execution:

- If the developer returns a custom drag shadow, the system's default drag shadow is no longer used.
- If the developer sets drag data, the system's default drag data is no longer used.

Text components [Search](./cj-text-input-search.md), [TextInput](./cj-text-input-textinput.md), [TextArea](./cj-text-input-textarea.md), [RichEditor](./cj-text-input-richeditor.md) do not support custom drag shadows when dragging selected text content. When `onDragStart` is used with menu preview or with components that have default drag-out support, custom content on the preview and menu items does not support dragging.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Initial Version:** 22

**Event Priority:** If the long-press trigger time < 500ms, the long-press event takes precedence over the drag event. If the long-press trigger time ≥ 500ms, the drag event takes precedence over the long-press event.

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| event | ?([DragInfo](./cj-common-types.md#class-draginfo)) -> [DragItemInfo](./cj-common-types.md#class-dragiteminfo) | Yes | - | Callback function triggered when dragging starts.<br/>Input parameter is drag event information, including drag point coordinates.<br/>Return parameter is the component information displayed during dragging. |

**Return Value:**

| Type | Description |
|:---|:---|
| T | Returns the generic method interface type. |

## func onDragStart(?(DragInfo) -> CustomBuilder)

```cangjie
func onDragStart(event: ?(DragInfo) -> CustomBuilder): T
```

**Function:** Overloaded drag event. Triggered when the component bound to this event is dragged for the first time, with a long-press duration ≥ 500ms and finger movement distance ≥ 10vp.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Initial Version:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| event | ?([DragInfo](./cj-common-types.md#class-draginfo)) -> [CustomBuilder](./cj-common-types.md#type-custombuilder) | Yes | - | Callback function triggered when dragging starts.<br/>Input parameter is drag event information, including drag point coordinates.<br/>Return parameter is the component information displayed during dragging, used in conjunction with [@Builder](../../arkui-cj/paradigm/cj-macro-builder.md) and the `bind` method. |

**Return Value:**

| Type | Description |
|:---|:---|
| T | Returns the generic method interface type. |

## func onDragStart(?(DragInfo) -> Unit)

```cangjie
func onDragStart(event: ?(DragInfo) -> Unit): T
```

**Function:** Overloaded drag event. Triggered when the component bound to this event is dragged for the first time, with a long-press duration ≥ 500ms and finger movement distance ≥ 10vp.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Initial Version:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| event | ?([DragInfo](./cj-common-types.md#class-draginfo)) -> Unit | Yes | - | Callback function triggered when dragging starts.<br/>Input parameter is drag event information, including drag point coordinates.<br/>Return parameter is the component information displayed during dragging. |

**Return Value:**

| Type | Description |
|:---|:---|
| T | Returns the generic method interface type. |

## func onDragEnter(?(DragInfo) -> Unit)

```cangjie
func onDragEnter(event: ?(DragInfo) -> Unit): T
```

**Function:** Triggered when dragging enters the component's bounds.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Initial Version:** 22

> **Note:**
>
> This event is only effective when the `onDrop` event is monitored.

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| event | ?([DragInfo](./cj-common-types.md#class-draginfo)) -> Unit | Yes | - | Callback function triggered when dragging enters the component's bounds.<br/>Input parameter is drag event information, including drag point coordinates. |

**Return Value:**

| Type | Description |
|:---|:---|
| T | Returns the generic method interface type. |

## func onDragMove(?(DragInfo) -> Unit)

```cangjie
func onDragMove(event: ?(DragInfo) -> Unit): T
```

**Function:** Triggered when dragging moves within the component's bounds.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Initial Version:** 22

> **Note:**
>
> This event is only effective when the `onDrop` event is monitored.

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| event | ?([DragInfo](./cj-common-types.md#class-draginfo)) -> Unit | Yes | - | Callback function triggered when dragging moves within the component's bounds. |

**Return Value:**

| Type | Description |
|:---|:---|
| T | Returns the generic method interface type. |

## func onDragLeave(?(DragInfo) -> Unit)

```cangjie
func onDragLeave(event: ?(DragInfo) -> Unit): T
```

**Function:** Triggered when dragging leaves the component's bounds.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Initial Version:** 22

> **Note:**
>
> This event is only effective when the `onDrop` event is monitored.

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| event | ?([DragInfo](./cj-common-types.md#class-draginfo)) -> Unit | Yes | - | Callback function triggered when dragging leaves the component's bounds.<br/>Input parameter is drag event information, including drag point coordinates. |

**Return Value:**

| Type | Description |
|:---|:---|
| T | Returns the generic method interface type. |

## func onDrop(?(DragInfo) -> Unit)

```cangjie
func onDrop(event: ?(DragInfo) -> Unit): T
```

**Function:** A component bound to this event can serve as a drag release target. Triggered when dragging stops within the component's bounds.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Initial Version:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| event | ?([DragInfo](./cj-common-types.md#class-draginfo)) -> Unit | Yes | - | Callback function triggered when dragging stops within the component's bounds.<br/>Input parameter is drag event information, including drag point coordinates. |

**Return Value:**

| Type | Description |
|:---|:---|
| T | Returns the generic method interface type. |