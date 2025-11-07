# Drag Control

Sets whether a component can respond to drag events.

> **Note:**
>
> The ArkUI framework provides default drag capabilities for the following components, supporting responses to data drag-out or drag-in operations. Developers can also customize drag responses by implementing generic drag events.
>
> - Components with default drag-out capability (data can be dragged from these components): [Search](./cj-text-input-search.md), [TextInput](./cj-text-input-textinput.md), [TextArea](./cj-text-input-textarea.md), [RichEditor](./cj-text-input-richeditor.md), [Text](./cj-text-input-text.md), [Image](./cj-image-video-image.md). Developers can control the use of default drag capabilities by setting the `draggable` property of these components.
>
> - Components with default drag-in capability (target components can respond to dragged-in data): [Search](./cj-text-input-search.md), [TextInput](./cj-text-input-textinput.md), [TextArea](./cj-text-input-textarea.md), [RichEditor](./cj-text-input-richeditor.md).
>
> For other components, developers need to set the `draggable` property to `true` and implement data transfer-related content in interfaces such as `onDragStart` to properly handle drag operations.
>
> The `Text` component must be used in conjunction with [copyOption](./cj-text-input-text.md#func-copyoptioncopyoptions), setting `copyOptions` to either `CopyOptions.InApp` or `CopyOptions.LocalDevice`.

## Import Module

```cangjie
import kit.ArkUI.*
```

## func dragPreview(String)

```cangjie
public func dragPreview(value: String): T
```

**Function:** Sets the preview image during component dragging.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Name | Type | Required | Default Value | Description |
|:---|:---|:---|:---|:---|
| value | String | Yes | - | The preview image during component dragging, effective only in `onDragStart` drag mode.<br/>When a component supports dragging and also has a preview image set via `bindContextMenu`, the long-press floating preview image will prioritize the one set by `bindContextMenu`. The background image returned by developers in `onDragStart` has lower priority than the preview image set by `dragPreview`. When a `dragPreview` image is set, it will be used as the background image during dragging.<br>When a string-type ID is passed, the screenshot of the corresponding component will be used as the preview image. If the component corresponding to the ID cannot be found, or if the component's `Visibility` property is set to `none`/`hidden`, the component itself will be screenshot for the drag preview. Currently, the screenshot does not include visual effects such as brightness, shadows, blur, or rotation.<br>Initial value: empty. |

**Return Value:**

| Type | Description |
|:---|:---|
| T | Returns the component instance itself that called this interface. |