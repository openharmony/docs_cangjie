# StepperItem

Used as a child component of the [Stepper](cj-navigation-switching-stepper.md) component.

## Import Module

```cangjie
import kit.ArkUI.*
```

## Child Components

Supports a single child component.

## Creating the Component

### init(() -> Unit)

```cangjie
public init(child: () -> Unit)
```

**Function:** Creates a child component for the [Stepper](cj-navigation-switching-stepper.md) component's page.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Initial Version:** 22

**Parameters:**

| Parameter | Type | Required | Default Value | Description |
|:---|:---|:---|:---|:---|
| child | () -> Unit | Yes | - | The child component of StepperItem. |

## Common Attributes/Common Events

Common Attributes: All supported.

Common Events: All supported.

## Component Attributes

### func nextLabel(?String)

```cangjie
public func nextLabel(value: ?String): This
```

**Function:** Sets the content of the right text button. The default value is "Start" for the last page and "Next" for other pages.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Initial Version:** 22

**Parameters:**

| Parameter | Type | Required | Default Value | Description |
|:---|:---|:---|:---|:---|
| value | ?String | Yes | - | The content of the right text button. If the string is too long, it will first shrink, then wrap (2 lines), and finally truncate.<br>Initial value: "". |

### func prevLabel(?String)

```cangjie
public func prevLabel(value: ?String): This
```

**Function:** Sets the content of the left text button. The first page does not have a left text button. When the stepper has more than one page, the default value for pages other than the first is "Back".

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Initial Version:** 22

**Parameters:**

| Parameter | Type | Required | Default Value | Description |
|:---|:---|:---|:---|:---|
| value | ?String | Yes | - | The content of the left text button. If the string is too long, it will first shrink, then wrap (2 lines), and finally truncate.<br>Initial value: "". |

### func status(?ItemState)

```cangjie
public func status(status!: ?ItemState = None): This
```

**Function:** Sets the display state of the stepper's nextLabel.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Initial Version:** 22

**Parameters:**

| Parameter | Type | Required | Default Value | Description |
|:---|:---|:---|:---|:---|
| status | ?[ItemState](./cj-common-types.md#enum-itemstate) | No | None | **Named parameter.** The display state of the stepper's nextLabel.<br>Initial value: ItemState.Normal. |

> **Notes:**
>
> - The StepperItem component does not support setting common width attributes; its width defaults to filling the parent Stepper component.
> - The StepperItem component does not support setting common height attributes; its height is determined by the parent Stepper component's height minus the label button component's height.

## Example Code

See [Stepper](cj-navigation-switching-stepper.md)