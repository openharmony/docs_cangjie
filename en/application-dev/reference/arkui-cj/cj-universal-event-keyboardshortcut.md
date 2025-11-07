# Component Keyboard Shortcut Events

Developers can set custom key combinations for components, with each component supporting multiple key combinations.

Even if a component is not focused or not displayed on its current page, it will respond to custom key combinations as long as it is mounted on the component tree of the focused window.

When setting key combinations, developers can also specify custom events. Pressing the key combination will trigger the custom event. If no custom event is set, the key combination behavior will be consistent with the click behavior.

## Import Module

```cangjie
import kit.ArkUI.*
```

## func keyboardShortcut(?FunctionKey, ?Array\<ModifierKey>)

```cangjie
func keyboardShortcut(value: ?FunctionKey, keys: ?Array<ModifierKey>): T
```

**Function:** Sets a keyboard shortcut for the component.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default Value | Description |
|:---|:---|:---|:---|:---|
| value | ?[FunctionKey](./cj-common-types.md#enum-functionkey) | Yes | - | Function key<br>Initial value: "". |
| keys | ?Array\<[ModifierKey](./cj-common-types.md#enum-modifierkey)> | Yes | - | Modifier key array |

**Return Value:**

| Type | Description |
|:---|:---|
| T | Returns the generic method interface type |

## func keyboardShortcut(?String, ?Array\<ModifierKey>)

```cangjie
func keyboardShortcut(value: ?String, keys: ?Array<ModifierKey>): T
```

**Function:** Sets a keyboard shortcut for the component.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default Value | Description |
|:---|:---|:---|:---|:---|
| value | ?String | Yes | - | Shortcut key string<br>Initial value: "". |
| keys | ?Array\<[ModifierKey](./cj-common-types.md#enum-modifierkey)> | Yes | - | Modifier key array |

**Return Value:**

| Type | Description |
|:---|:---|
| T | Returns the generic method interface type |

## func keyboardShortcut(?FunctionKey, ?Array\<ModifierKey>, ?() -> Unit)

```cangjie
func keyboardShortcut(value: ?FunctionKey, keys: ?Array<ModifierKey>, action: ?() -> Unit): T
```

**Function:** Sets a keyboard shortcut for the component and specifies the triggered action.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default Value | Description |
|:---|:---|:---|:---|:---|
| value | ?[FunctionKey](./cj-common-types.md#enum-functionkey) | Yes | - | Function key<br>Initial value: "". |
| keys | ?Array\<[ModifierKey](./cj-common-types.md#enum-modifierkey)> | Yes | - | Modifier key array |
| action | ?() -> Unit | Yes | - | Triggered action |

**Return Value:**

| Type | Description |
|:---|:---|
| T | Returns the generic method interface type |

## func keyboardShortcut(?String, ?Array\<ModifierKey>, ?() -> Unit)

```cangjie
func keyboardShortcut(value: ?String, keys: ?Array<ModifierKey>, action: ?() -> Unit): T
```

**Function:** Sets a keyboard shortcut for the component and specifies the triggered action.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default Value | Description |
|:---|:---|:---|:---|:---|
| value | ?String | Yes | - | Shortcut key string<br>Initial value: "". |
| keys | ?Array\<[ModifierKey](./cj-common-types.md#enum-modifierkey)> | Yes | - | Modifier key array |
| action | ?() -> Unit | Yes | - | Triggered action |

**Return Value:**

| Type | Description |
|:---|:---|
| T | Returns the generic method interface type |

## Notes on Using Keyboard Shortcuts

Keyboard shortcuts respond to system key presses and take precedence over ordinary key events (OnKeyEvent). For details on the logic of key event triggering, see [Key Events](../../arkui-cj/cj-common-events-device-input-event.md#key-events).

| Scenario | Shortcut Handling Logic | Example |
|:---|:---|:---|
| All components supporting onClick events | Support custom key combinations | None |
| Custom key combination requirements | Control keys Ctrl, Shift, Alt, and their combinations with other input character keys | Button("button1").keyboardShortcut("a",\[ModifierKey.CTRL]) |
| Multiple components set with the same key combination | Only the first component in the node tree responds; others do not. | Button("button1").keyboardShortcut("a",\[ModifierKey.CTRL])<br>Button("button2").keyboardShortcut("a",\[ModifierKey.CTRL]) |
| Regardless of whether the component is focused | The shortcut will respond as long as the window is focused | None |
| When binding a single shortcut, if the value or keys parameter (or both) of the keyboardShortcut interface is empty.<br>When binding multiple shortcuts, shortcuts cannot be canceled. | Cancel shortcut settings | Button("button1").keyboardShortcut("",\[ModifierKey.CTRL])<br>Button("button2").keyboardShortcut("a",\[])<br>Button("button3").keyboardShortcut("",\[]) |
| When independent pipeline sub-windows and main windows coexist | The focused window responds to shortcuts | None |
| Ctrl, Shift, Alt in the keys parameter of the keyboardShortcut interface | Both left and right keys are responded to | Button("button1").keyboardShortcut("a",\[ModifierKey.CTRL, ModifierKey.ALT]) |
| Single-character value in the keyboardShortcut interface | Case-insensitive | Button("button1").keyboardShortcut("a",\[ModifierKey.CTRL])<br>Button("button2").keyboardShortcut("A",\[ModifierKey.CTRL]) |
| Shortcut response | Responds to all shortcut down states and continuously responds | None |
| Hidden components | Respond to shortcuts | None |
| Disabled components | Do not respond to shortcuts | None |
| 1\. When component key combinations (including system predefined shortcuts) are the same.<br>2\. When the value parameter of the interface has multiple characters.<br>3\. When the keys parameter has duplicate control keys. | These cases do not bind key combinations; previously bound key combinations remain valid. | Button("button1").keyboardShortcut("c",\[ModifierKey.CTRL])<br>Button("button2").keyboardShortcut("ab",\[ModifierKey.CTRL])<br>Button("button3").keyboardShortcut("ab",\[ModifierKey.CTRL,ModifierKey.CTRL]) |

## System Shortcuts That Cannot Be Bound

The following key combinations cannot be bound as shortcuts:

- Alt + F4
- Alt + Shift + F4
- Alt + TAB
- Alt + Shift + TAB
- Ctrl + Shift + ESC

## Existing System Key Events

The following system key events already exist, with specifications as shown in the table below.

These key events have priority relationships with custom key events. Higher-priority events will intercept lower-priority ones. For details on focus event response priorities, see [Key Events](../../arkui-cj/cj-common-events-device-input-event.md#key-events).

| Shortcut | Focused Component | Purpose | Event Handling Category |
|:---|:---|:---|:---|
| Arrow keys, Shift + Arrow keys | Input components | Move cursor | Input method |
| Arrow keys, Shift + Arrow keys | General components | When the system is in focus navigation mode, used for directional navigation | System keys |
| TAB, Shift + TAB | General components | Trigger focus navigation mode / navigation | System keys |