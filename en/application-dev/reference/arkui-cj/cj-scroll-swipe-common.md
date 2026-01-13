# Universal Scroll Component API

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

Common properties and events for scroll components are currently only supported by [List](./cj-scroll-swipe-list.md), [Grid](./cj-scroll-swipe-grid.md), and [Scroll](./cj-scroll-swipe-scroll.md).

## Component Properties

### func scrollBar(?BarState)

```cangjie
public func scrollBar(barState: ?BarState): T
```

**Function:** Sets the scroll bar state.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| barState | ?[BarState](./cj-common-types.md#enum-barstate) | Yes | - | Scroll bar state.<br>Initial value:<br>For List, Grid, and Scroll components: BarState.Auto. |

### func scrollBarColor(?ResourceColor)

```cangjie
public func scrollBarColor(color: ?ResourceColor): T
```

**Function:** Sets the scroll bar color.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| color | ?[ResourceColor](./cj-common-types.md#interface-resourcecolor) | Yes | - | Scroll bar color.<br>Initial value: 0x182431 (40% opacity). HEX format color, supports rgb or argb, e.g., 0xffffff. |

### func scrollBarWidth(?Length)

```cangjie
public func scrollBarWidth(value: ?Length): T
```

**Function:** Sets the scroll bar width (percentage not supported). After setting, both normal and pressed states will use this width. If the width exceeds the main axis height of the scroll component, it reverts to the initial value.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| value | ?[Length](./cj-common-types.md#interface-length) | Yes | - | Scroll bar width.<br>Initial value: 4<br>Unit: vp<br>Range: Values < 0 use the initial value. 0 hides the scroll bar. |

### func clipContent(?ContentClipMode)

```cangjie
public func clipContent(clip: ?ContentClipMode): T
```

**Function:** Sets the clipping region for the scroll container's content layer.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| clip | ?[ContentClipMode](./cj-scroll-swipe-scroll.md#enum-contentclipmode) | Yes | - | Clipping applies only to the scroll container's content (child nodes), not the background.<br>Initial value: ContentClipMode.Boundary for Grid and Scroll, ContentClipMode.ContentOnly for List. |

### func clipContent(?RectShape)

```cangjie
public func clipContent(clip: ?RectShape): T
```

**Function:** Sets the clipping region for the scroll container's content layer.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| clip | ?[RectShape](./cj-apis-shape.md#class-rectshape) | Yes | - | Clipping applies only to the scroll container's content (child nodes), not the background. When using RectShape, only width, height, and [offset](./cj-universal-attribute-location.md#func-offsetlength-length) relative to the component's top-left corner are supported; rounded corners are not. |

### func enableScrollInteraction(?Bool)

```cangjie
public func enableScrollInteraction(value: ?Bool): T
```

**Function:** Enables or disables scroll gestures.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| value | ?Bool | Yes | - | Whether scroll gestures are enabled. When false, scrolling via touch or mouse is disabled, but the [Scroller](./cj-scroll-swipe-scroll.md#class-scroller) controller's scroll APIs remain functional.<br>Initial value: true. |

### func fadingEdge(Option\<Bool>)

```cangjie
public func fadingEdge(enabled: Option<Bool>): T
```

**Function:** Enables edge fading effect and sets its length.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| enabled | Option\<Bool> | Yes | - | When fadingEdge is enabled, it overrides the component's .overlay() property.<br>Avoid setting background properties on the component when fadingEdge is enabled, as it may affect the fading effect.<br>When fadingEdge is enabled, the component is clipped to its bounds; setting clip to false has no effect.<br>Initial value: false (edge fading disabled). |

### func fadingEdge(Option\<Bool>,?FadingEdgeOptions)

```cangjie
public func fadingEdge(enabled: Option<Bool>, options: ?FadingEdgeOptions): T
```

**Function:** Enables edge fading effect and sets its length.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| enabled | Option\<Bool> | Yes | - | When fadingEdge is enabled, it overrides the component's .overlay() property.<br>Avoid setting background properties on the component when fadingEdge is enabled, as it may affect the fading effect.<br>When fadingEdge is enabled, the component is clipped to its bounds; setting clip to false has no effect.<br>Initial value: false (edge fading disabled). |
| options | ?[FadingEdgeOptions](./cj-scroll-swipe-scroll.md#class-fadingedgeoptions) | Yes | - | Edge fading parameters object. Used to define edge fading properties, such as fading length. |

### func flingSpeedLimit(?Float64)

```cangjie
public func flingSpeedLimit(speedLimit: ?Float64): T
```

**Function:** Limits the maximum initial speed when a fling animation starts after touch scrolling ends.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| speedLimit | ?Float64 | Yes | - | Maximum initial speed for fling animation.<br>Initial value: 9000.0<br>Unit: vp/s<br>Range: (0, +∞). Values ≤ 0 use the initial value. |

### func friction(?Float64)

```cangjie
public func friction(value: ?Float64): T
```

**Function:** Sets the friction coefficient, effective during manual scrolling. Affects only inertial scrolling and indirectly impacts chained effects during inertial scrolling. Values ≤ 0 use the initial value.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| value | ?Float64 | Yes | - | Friction coefficient.<br>Initial value: 0.75 for non-wearable devices, 0.9 for wearables.<br>Range: (0, +∞). Values ≤ 0 use the initial value. |

### func friction(?AppResource)

```cangjie
public func friction(value: ?AppResource): T
```

**Function:** Sets the friction coefficient, effective during manual scrolling. Affects only inertial scrolling and indirectly impacts chained effects during inertial scrolling. Values ≤ 0 use the initial value.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| value | ?[AppResource](../LocalizationKit/cj-apis-resource.md#class-appresource) | Yes | - | Friction coefficient.<br>Initial value: 0.75 for non-wearable devices, 0.9 for wearables.<br>Range: (0, +∞). Values ≤ 0 use the initial value. |

### func nestedScroll(?NestedScrollOptions)

```cangjie
public func nestedScroll(value: ?NestedScrollOptions): T
```

**Function:** Sets nested scroll modes for forward and backward directions to achieve coordinated scrolling with parent components.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| value | ?[NestedScrollOptions](./cj-scroll-swipe-scroll.md#class-nestedscrolloptions) | Yes | - | Nested scroll options. |

## Component Events

### func onDidScroll(?OnScrollCallBack)

```cangjie
public func onDidScroll(handler: ?OnScrollCallBack): T
```

**Function:** Triggered when the scroll component is scrolled, returning the current frame's scroll offset and scroll state.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| handler | ?[OnScrollCallBack](./cj-scroll-swipe-scroll.md#type-onscrollcallback) | Yes | - | Callback triggered when scrolling.<br>Parameter 1: Scroll offset per frame (positive when scrolling up, negative when scrolling down). Unit: vp.<br>Parameter 2: Current scroll state. |

### func onReachEnd(?() -> Unit)

```cangjie
public func onReachEnd(event: ?() -> Unit): T
```

**Function:** Triggered when the scroll component reaches the end position. For spring edge effects, triggered once when scrolling past the end and again when bouncing back.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| event | ?() -> Unit | Yes | - | Callback triggered when reaching the end position. |

### func onReachStart(?() -> Unit)

```cangjie
public func onReachStart(event: ?() -> Unit): T
```

**Function:** Triggered when the scroll component reaches the start position. Triggered once during initialization and again when scrolling to the start. For spring edge effects, triggered once when scrolling past the start and again when bouncing back.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| event | ?() -> Unit | Yes | - | Callback triggered when reaching the start position. |

### func onScrollStart(?() -> Unit)

```cangjie
public func onScrollStart(event: ?() -> Unit): T
```

**Function:** Triggered when scrolling starts. Occurs when dragging the scroll component or its scroll bar, or when an animated scroll via [Scroller](./cj-scroll-swipe-scroll.md#class-scroller) begins.

Trigger conditions:<br>
1. Triggered when scrolling starts (supports other input methods like keyboard/mouse).<br>
2. Triggered when a scroll controller API call initiates an animated transition.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| event | ?() -> Unit | Yes | - | Callback triggered when scrolling starts. |

### func onScrollStop(?() -> Unit)

```cangjie
public func onScrollStop(event: ?() -> Unit): T
```

**Function:** Triggered when scrolling stops. Occurs after touch/mouse scrolling ends or when an animated scroll via [Scroller](./cj-scroll-swipe-scroll.md#class-scroller) completes.

Trigger conditions:<br>
1. Triggered after scrolling stops (supports other input methods like keyboard/mouse).<br>
2. Triggered when a scroll controller API call completes an animated transition.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| event | ?() -> Unit | Yes | - | Callback triggered when scrolling stops. |

### func onWillScroll(Option\<(Float64,ScrollState,ScrollSource) -> ScrollResult>)

```cangjie
public func onWillScroll(handler: Option<(Float64, ScrollState, ScrollSource) -> ScrollResult>): T
```

**Function:** Scroll event callback triggered before scrolling begins. Returns the calculated scroll offset (not the final value), current scroll state, and scroll source. The callback's return value can specify the intended scroll offset.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| handler | Option\<(Float64, [ScrollState](./cj-common-types.md#enum-scrollstate), [ScrollSource](./cj-common-types.md#enum-scrollsource)) -> [ScrollResult](./cj-scroll-swipe-scroll.md#class-scrollresult)> | Yes | - | Callback triggered before scrolling.<br>Parameter 1: Scroll offset per frame (positive when scrolling up, negative when scrolling down). Unit: vp.<br>Parameter 2: Current scroll state.<br>Parameter 3: Scroll operation source.<br>Return value: Intended scroll offset (unit: vp). |

> **Note:**
>
> Does not trigger when calling scrollEdge or scrollToIndex without animation.

### func onWillScroll(Option\<(Float64,ScrollState,ScrollSource) -> Unit>)

```cangjie
public func onWillScroll(handler: Option<(Float64, ScrollState, ScrollSource) -> Unit>): T
```

**Function:** Scroll event callback triggered before scrolling begins. Returns the calculated scroll offset (not the final value), current scroll state, and scroll source.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| handler | Option<(Float64, [ScrollState](./cj-common-types.md#enum-scrollstate), [ScrollSource](./cj-common-types.md#enum-scrollsource)) -> Unit> | Yes | - | Callback triggered before scrolling. |

> **Note:**
>
> Does not trigger when calling scrollEdge or scrollToIndex without animation.