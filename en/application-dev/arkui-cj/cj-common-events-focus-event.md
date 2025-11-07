# Focus Events

## Basic Concepts and Specifications

### Basic Concepts

#### Focus, Focus Chain, and Focus Navigation

- **Focus**: Refers to the single interactive element currently highlighted in the application interface. When users interact indirectly with the application using non-pointing input devices such as keyboards, TV remotes, or car joysticks/knobs, focus-based navigation and interaction become essential input methods.
- **Focus Chain**: In the component tree structure of an application, when a component gains focus, all nodes along the path from the root node to that component node are considered in a focused state, forming a continuous focus chain.
- **Focus Navigation**: Refers to the behavior of transferring focus between components within the application. This process is transparent to users, but developers can monitor these changes by listening to the [`onFocus`](../reference/arkui-cj/cj-universal-event-focus.md#func-onfocus---unit) (focus gain) and [`onBlur`](../reference/arkui-cj/cj-universal-event-focus.md#func-onblur---unit) (focus loss) events. For specific methods and rules of focus navigation, see [Focus Navigation Specifications](#focus-navigation-specifications).

#### Focus State

Indicates the style of the currently focused component.

- **Display Rules**: By default, the focus state is not displayed. It only becomes visible when the application enters the active state. Therefore, while a focused component may not display the focus state (depending on whether it is active), a component displaying the focus state must be focused. Most components have built-in focus state styles, but developers can also customize them using style interfaces. Once customized, the component will no longer display the built-in focus state style. In a focus chain, if multiple components have focus states, the system adopts a child-first strategy, prioritizing the display of the child component's focus state and showing only one focus state at a time.
- **Entering Active State**: The focus active state is entered by pressing the TAB key on an external keyboard or using the `FocusController.activate(true)` method. Once active, keyboard TAB or arrow keys can be used for focus navigation. The first TAB key press used to activate the focus state does not trigger focus navigation.
- **Exiting Active State**: The focus active state exits when the application receives the `FocusController.active(false)` method or a click event (including touchscreen press events and left mouse button press events).

#### Hierarchical Pages

Hierarchical pages are a collective term for specific container components in the focus framework, including Page, Dialog, SheetPage, ModalPage, Menu, Popup, Dialog, NavBar, and NavDestination. These components typically share the following key characteristics:

- **Visual Hierarchy Independence**: Visually, these components are independent of other page content and usually appear above it, creating a visual hierarchy.
- **Focus Following**: When such a component is first created and displayed, it immediately captures the application's focus.
- **Focus Navigation Scope Limitation**: When focus is within these components, users cannot transfer focus to elements outside the component via keyboard inputs; focus movement is restricted to the component's interior.

At any time, an application must have at least one hierarchical page component holding the current focus. When this hierarchical page is closed or becomes invisible, focus automatically transfers to the next available hierarchical page component, ensuring continuity and consistency in user interaction.

> **Note:**
>
> - The [Popup](./cj-popup-and-menu-components-popup.md) component does not exhibit the second characteristic when its [`focusable`](../reference/arkui-cj/cj-universal-attribute-focus.md#focusablebool) attribute (a component attribute, not a universal attribute) is set to `false`.
> - NavBar and [NavDestination](../reference/arkui-cj/cj-navigation-switching-navdestination.md#navdestination) do not exhibit the third characteristic. Their focus navigation scope is the same as that of their first parent hierarchical page.

#### Root Container

The root container is a concept within [hierarchical pages](#hierarchical-pages). When a [hierarchical page](#hierarchical-pages) is first created and displayed, focus is immediately captured by that page. The end node of the focus chain for that [hierarchical page](#hierarchical-pages) becomes the default focus, which typically resides on the root container of the page.

By default, the default focus of a [hierarchical page](#hierarchical-pages) is on its root container, but developers can customize this behavior using the `defaultFocus` attribute.

When focus is on the root container, the first TAB key press not only activates the focus state but also triggers focus transfer to child components. If the child component is also a container, focus continues to propagate downward until it reaches a leaf node. The propagation rule is: prioritize transferring focus to the last focused child node; if none exists, transfer to the first child node by default.

### Focus Navigation Specifications

Focus navigation can be categorized into active and passive navigation based on the triggering method.

#### Active Focus Navigation

Refers to focus movement caused by intentional actions of developers or users, including:

- **Keyboard Navigation**: Using TAB/Shift+TAB/arrow keys on an external keyboard.
- **Programmatic Focus Request**: Using [`requestFocus`](../reference/arkui-cj/cj-universal-attribute-focus.md#static-func-requestfocusstring) to request focus.
- **Click-to-Focus**: Using [`focusOnTouch`](../reference/arkui-cj/cj-universal-attribute-focus.md#func-focusontouchbool) to enable focus acquisition via clicks.

- **Keyboard Navigation**:
    - **Prerequisite**: The application must be in the focus active state.
    - **Scope Limitation**: Keyboard navigation is restricted to the currently focused [hierarchical page](#hierarchical-pages). For details, see the "Focus Navigation Scope Limitation" section under [hierarchical pages](#hierarchical-pages).
    - **Key Types**:
        - **TAB Key**: Follows a Z-shaped traversal logic, iterating through all leaf nodes within the current scope. After reaching the last component, pressing TAB again cycles focus back to the first focusable component, enabling cyclic navigation.
        - **Shift+TAB Key**: Produces the opposite effect of the TAB key.
        - **Arrow Keys (Up/Down/Left/Right)**: Follows a cross-shaped movement strategy. In a single-layer container, focus transfer is determined by the container's specific navigation algorithm. If the algorithm determines the next focus should land on a container component, the system uses a center-point distance priority algorithm to identify the target child node within the container.
    - **Navigation Algorithm**: Each focusable container component has its own navigation algorithm defining focus transfer rules.
    - **Child-First**: When a child component handles keyboard navigation events, the parent component does not intervene.

- **requestFocus**:
    For details, see [Active Focus Acquisition/Loss](#active-focus-acquisitionloss). This method actively transfers focus to a specified component.
    - Cannot cross windows or ArkUI instances but can cross [hierarchical pages](#hierarchical-pages).

- **focusOnTouch**:
    For details, see [`focusOnTouch`](../reference/arkui-cj/cj-universal-attribute-focus.md#func-focusontouchbool). Enables a component to gain focus upon clicking. If the component itself is not focusable, this feature is ineffective. If applied to a container component, clicking prioritizes transferring focus to the last focused child component; otherwise, it transfers to the first focusable child component.

#### Passive Focus Navigation

Passive focus navigation refers to automatic focus transfer triggered by the system or other operations without direct developer intervention. This is the default behavior of the focus system.

Current mechanisms for passive focus navigation include:

- **Component Deletion**: When a focused component is deleted, the focus framework first attempts to transfer focus to adjacent sibling components, following a back-to-front order. If no siblings are focusable, focus is released, and the parent component is notified to handle focus.
- **Attribute Changes**: If the `focusable` or `enabled` attribute of a focused component is set to `false`, or its `visibility` attribute is set to non-visible, the focus framework automatically transfers focus to another focusable component. The framework first attempts to transfer focus to adjacent siblings (back-to-front). If no siblings are focusable, focus is released, and the parent component is notified.
- **[Hierarchical Page](#hierarchical-pages) Switching**: When switching between [hierarchical pages](#hierarchical-pages), such as navigating from one page to another, the current page's focus is automatically released, and the new page may gain focus based on preset logic.
- **Web Component Initialization**: For Web components, if designed to immediately gain focus upon creation (e.g., certain pop-ups or input fields), focus may transfer to the Web component. This behavior is part of the component's logic and not within the focus framework's specifications.

### Focus Navigation Algorithms

In the focus management system, each focusable container is equipped with specific navigation algorithms that define how focus transfers from the currently focused child component to the next when using TAB, Shift+TAB, or arrow keys.

The choice of algorithm depends on the container's UX (User Experience) specifications and is adapted by the container component. Currently, the focus framework supports three navigation algorithms: Linear Navigation, Projection Navigation, and Custom Navigation.

#### Linear Navigation Algorithm

The default navigation strategy, linear navigation is based on the mounting order of child nodes in the container's node tree. It is commonly used for unidirectional layouts like Row, Column, and Flex containers. Rules:

- **Order Dependency**: Navigation order is entirely based on the mounting order of child nodes, independent of their actual layout positions.
- **TAB Key Navigation**: Pressing TAB traverses child nodes in mounting order.
- **Arrow Key Navigation**: Arrow keys perpendicular to the container's defined direction are ignored. For example, in a horizontal Row container, up/down arrow keys are ineffective.
- **Boundary Handling**: When focus is on the first or last child node, the container rejects arrow key requests in the opposite direction. For example, in a horizontal Row container, pressing the left arrow key when focus is on the first child node is ignored.

#### Projection Navigation Algorithm

Projection navigation is based on the projection of the currently focused component in the navigation direction, combined with overlap area and center-point distance calculations for determining the next focus. This algorithm is particularly suitable for containers with unevenly sized child components, currently only Flex containers with the `wrap` attribute. Rules:

- **Rule 1 (Arrow Keys)**: For arrow key navigation, calculate the overlap area between the projection and child component regions. Among all child components with non-zero overlap, the one with the shortest straight-line distance from the current focused component's center point wins. If multiple candidates exist, the one earlier in the node tree wins. If no overlaps exist, the container cannot process the arrow key request.
- **Rule 2 (TAB Key)**: First apply Rule 1 using the right arrow direction. If successful, exit. Otherwise, simulate moving the current focused child component downward by its height, then apply Rule 1 using the left arrow direction. The child component with the farthest straight-line distance and overlap wins. If no overlaps exist, the TAB key request is ignored.
- **Rule 3 (Shift+TAB Key)**: First apply Rule 1 using the left arrow direction. If successful, exit. Otherwise, simulate moving the current focused child component upward by its height, then apply Rule 1 using the right arrow direction. The child component with the farthest straight-line distance and overlap wins. If no overlaps exist, the Shift+TAB key request is ignored.

#### Custom Navigation Algorithm

A navigation algorithm customized by the component, with specifications defined by the component itself.

## Focus/Blur Events

```cangjie
public func onFocus(event: ?() -> Unit): T
```

Focus event callback. Triggered when the bound component gains focus.

```cangjie
public func onBlur(event: ?() -> Unit): T 
```

Blur event callback. Triggered when the bound component loses focus.

The `onFocus` and `onBlur` interfaces are typically used in pairs to monitor component focus changes.

 <!-- run -->

```cangjie
package ohos_app_cangjie_entry
import kit.ArkUI.*
import ohos.arkui.state_macro_manage.*

@Entry
@Component
class EntryView {
    @State var oneButtonColor: Color = Color.Gray
    @State var twoButtonColor: Color = Color.Gray
    @State var threeButtonColor: Color = Color.Gray
    func build() {
        Column(space: 20) {
        // Using up/down arrow keys on an external keyboard moves focus between the three buttons. Button color changes on focus and reverts on blur.
        Button("First Button")
            .backgroundColor(oneButtonColor)
            .width(260)
            .height(70)
            .fontColor(Color.Black)
            // Monitor focus event for the first component; change color on focus.
            .onFocus({ =>
                oneButtonColor = Color.Green
            })
            // Monitor blur event for the first component; revert color on blur.
            .onBlur({=>
                oneButtonColor = Color.Gray
            })
        Button("Second Button")
            .backgroundColor(twoButtonColor)
            .width(260)
            .height(70)
            .fontColor(Color.Black)
            // Monitor focus event for the second component; change color on focus.
            .onFocus({=>
                twoButtonColor = Color.Green
            })
            // Monitor blur event for the second component; revert color on blur.
            .onBlur({=>
                twoButtonColor = Color.Gray
            })
        Button("Third Button")
            .backgroundColor(threeButtonColor)
            .width(260)
            .height(70)
            .fontColor(Color.Black)
            // Monitor focus event for the third component; change color on focus.
            .onFocus({=>
                threeButtonColor = Color.Green
            })
            // Monitor blur event for the third component; revert color on blur.
            .onBlur({=>
                threeButtonColor = Color.Gray
            })
        }.width(100.percent).margin(top: 20)
    }
}
```

![onFocus](figures/onFocus.gif)

The above example includes the following steps:

1. The application opens. Pressing the TAB key activates focus navigation. "First Button" displays the focus state style: a blue outline around the component. The `onFocus` callback is triggered, changing the background color to green.
2. Pressing the TAB key triggers focus navigation. "Second Button" gains focus, triggering its `onFocus` callback (background turns green). "First Button" loses focus, triggering its `onBlur` callback (background reverts to gray).
3. Pressing the TAB key again triggers focus navigation. "Third Button" gains focus, triggering its `onFocus` callback (background turns green). "Second Button" loses focus, triggering its `onBlur` callback (background reverts to gray).

## Setting Component Focusability

```cangjie
public func focusable(value: ?Bool): T
```

Sets whether a component can receive focus.

Components can be broadly categorized into three types based on focusability:

1. **Default Focusable Components**: Typically interactive components like Button, Checkbox, and TextInput. These components are focusable by default without any additional attributes.
2. **Focusable but Not by Default**: Examples include Text and Image components. These are not focusable by default but can be enabled using the universal attribute `focusable(true)`. If such a component has no `focusable` attribute but is configured with `onClick` or a single-finger Tap gesture, it implicitly becomes focusable. If its `focusable` attribute is set to `false`, it remains non-focusable even with these events.
3. **Non-Focusable Components**: Typically display-only components like Blank and Circle. These cannot be made focusable even with the `focusable` attribute.

```cangjie
public func enabled(value: ?Bool): T
```

Setting the interactive attribute [`enabled`](../reference/arkui-cj/cj-universal-attribute-enable.md#func-enabledbool) to `false` makes the component non-interactive and non-focusable.

```cangjie
public func visibility(value: ?Bool): T
```

Setting the visibility attribute [`visibility`](../reference/arkui-cj/cj-universal-attribute-visibility.md#func-visibilityvisibility) to `Visibility.None` or `Visibility.Hidden` makes the component invisible and non-focusable.

```cangjie
public func focusOnTouch(value: ?Bool): T
```

Sets whether the current component supports focus acquisition via clicks.

> **Note:**
>
> When a focused component's `focusable` or `enabled` attribute is set to `false`, it automatically loses focus, and focus is transferred to another component according to the [Focus Navigation Specifications](#focus-navigation-specifications).

 <!-- run -->

```cangjie
package ohos_app_cangjie_entry
import kit.ArkUI.*
import ohos.arkui.state_macro_manage.*

@Entry
@Component
class EntryView {
    @State var textFocusable: Bool = true
    @State var textEnabled: Bool = true
    @State var color1: Color = Color(0xFFFF00)
    @State var color2: Color = Color(0xFFFF00)
    @State var color3: Color = Color(0xFFFF00)

    func build() {
        Column(space: 5) {
            // First Text component without focusable attribute; non-focusable by default.
            Text("Default Text")
                .borderColor(color1)
                .borderWidth(2)
                .width(300)
                .height(70)
                .onFocus({ =>
                    color1 = Color.Blue
                })
                .onBlur({ =>
                    color1 = Color(0xFFFF00)
                })

            Divider()

            // Second Text with initial focusable=true and focusOnTouch=true.
            Text("focusable: " + textFocusable.toString())
                .borderColor(color2)
                .borderWidth(2)
                .width(300)
                .height(70)
                .focusable(textFocusable)
                .focusOnTouch(true)
                .onFocus({ =>
                    color2 = Color.Blue
                })
                .onBlur({ =>
                    color2 = Color(0xFFFF00)
                })

            // Third Text with focusable=true and initial enabled=true.
            Text("enabled: " + textEnabled.toString())
                .borderColor(color3)
                .borderWidth(2)
                .width(300)
                .height(70)
                .focusable(true)
                .enabled(textEnabled)
                .focusOnTouch(true)
                .onFocus({ =>
                    color3 = Color.Blue
                })
                .onBlur({ =>
                    color3 = Color(0xFFFF00)
                })

            Divider()

            Row() {
                Button("Button1")
                    .width(140).height(70)
                Button("Button2")
                    .## Active Focus Acquisition/Loss

Using methods from the FocusControl:

```cangjie
public static func requestFocus(value: ?String): Bool
```

Calling this interface actively transfers focus to the component specified by the parameter. The focus transfer takes effect at the next frame signal.

<!-- run -->

```cangjie
package ohos_app_cangjie_entry
import kit.ArkUI.*
import ohos.arkui.state_macro_manage.*

@Entry
@Component
class EntryView {
    @State var btColor: UInt32 = 0x2787d9
    @State var btColor2: UInt32 = 0x2787d9

    func build() {
        Column(space: 20) {
            Column(space: 5) {
                Button("Button")
                    .width(200)
                    .height(70)
                    .fontColor(Color.White)
                    .focusOnTouch(true)
                    .backgroundColor(0x2787d9)
                    .onFocus({ =>
                        btColor = 0xd5d5d5
                    })
                    .onBlur({ =>
                        btColor = 0x2787d9
                    })
                    .id("testButton")

                Button("Button")
                    .width(200)
                    .height(70)
                    .fontColor(Color.White)
                    .focusOnTouch(true)
                    .backgroundColor(btColor2)
                    .onFocus({ =>
                        btColor2 = 0xd5d5d5
                    })
                    .onBlur({ =>
                        btColor2 = 0x2787d9
                    })
                    .id("testButton2")

                Divider()
                    .vertical(false)
                    .width(80.percent)
                    .backgroundColor(0x707070)
                    .height(10)
                //Clicking the FocusControl.requestFocus button gives focus to the second Button.
                Button("FocusControl.requestFocus")
                    .width(200)
                    .height(70)
                    .fontColor(Color.White)
                    .onClick({ evt =>
                        FocusControl.requestFocus("testButton2")
                    })
                    .backgroundColor(0xff2787d9)
            }
        }
        .width(100.percent)
        .height(100.percent)
    }
}
```

![focus-2](figures/focus-2.gif)

## Focus and Key Events

When a component gains focus and has a click event (`onClick`) or single-finger tap event (`TapGesture`), pressing Enter or Space will trigger the corresponding event callback.

> **Note:**
>
> - When a click event (`onClick`) or single-finger tap event (`TapGesture`) is triggered by Enter or Space, the event does not bubble up by default, meaning the parent component's corresponding [key event](../reference/arkui-cj/cj-universal-event-key.md) will not be triggered simultaneously.
> - Key events (`onKeyEvent`) bubble up by default, meaning the parent component's key event callback will also be triggered.
> - If a component has both a click event (`onClick`) and a key event (`onKeyEvent`), both will respond when Enter or Space is pressed.
> - A focused component responding to a click event (`onClick`) is independent of the focus active state.

<!-- run -->

```cangjie
package ohos_app_cangjie_entry
import kit.ArkUI.*
import ohos.arkui.state_macro_manage.*

@Entry
@Component
class EntryView {
    @State var count: Int = 0
    @State var name: String = "Button"

    func build() {
        Column {
            Button(name)
                .fontSize(30)
                .onClick({ evt =>
                    count++
                    if (count <= 0) {
                        name = "count is negative number"
                    } else if (count % 2 == 0) {
                        name = "count is even number"
                    } else {
                        name = "count is odd number"
                    }
                })
                .height(60)
        }
        .height(100.percent).width(100.percent).justifyContent(FlexAlign.Center)
    }
}
```

![focus-4](figures/focus-4.gif)

## Component Focus Capability Description

Basic component focus capabilities are as follows:

| Basic Component                                     | Has Focus Capability | Default focusable Value |
| :---------------------------------------- | :------- | :------------ |
| [AlphabetIndexer](../reference/arkui-cj/cj-information-display-alphabetindexer.md) | Yes       | true         |
| [Blank](../reference/arkui-cj/cj-blank-divider-blank.md) | No       | false        |
| [Button](../reference/arkui-cj/cj-button-picker-button.md) | Yes       | true         |
| [Checkbox](../reference/arkui-cj/cj-button-picker-checkbox.md) | Yes       | true         |
| [CheckboxGroup](../reference/arkui-cj/cj-button-picker-checkboxgroup.md) | Yes       | true         |
| [DataPanel](../reference/arkui-cj/cj-information-display-datapanel.md) | Yes       | false        |
| [DatePicker](../reference/arkui-cj/cj-button-picker-datepicker.md) | Yes       | true         |
| [Divider](../reference/arkui-cj/cj-blank-divider-divider.md) | Yes       | false        |
| [Gauge](../reference/arkui-cj/cj-information-display-gauge.md) | Yes       | false        |
| [Image](../reference/arkui-cj/cj-image-video-image.md) | Yes       | false        |
| [ImageSpan](../reference/arkui-cj/cj-text-input-imagespan.md)                 | No       | false        |
| [LoadingProgress](../reference/arkui-cj/cj-information-display-loadingprogress.md) | Yes       | true        |
| [Navigation](../reference/arkui-cj/cj-navigation-switching-navigation.md) | Yes       | true         |
| [PatternLock](../reference/arkui-cj/cj-information-display-patternlock.md) | Yes       | true        |
| [Progress](../reference/arkui-cj/cj-information-display-progress.md) | Yes       | true        |
| [QRCode](../reference/arkui-cj/cj-information-display-qrcode.md) | Yes       | true        |
| [Radio](../reference/arkui-cj/cj-button-picker-radio.md) | Yes       | true         |
| [Rating](../reference/arkui-cj/cj-button-picker-rating.md) | Yes       | true         |
| [RichEditor](../reference/arkui-cj/cj-text-input-richeditor.md) | Yes       | true         |
| [RichText](../reference/arkui-cj/cj-text-input-richtext.md) | No       | false        |
| [ScrollBar](../reference/arkui-cj/cj-scroll-swipe-scrollbar.md) | No       | false        |
| [Search](../reference/arkui-cj/cj-text-input-search.md) | Yes       | true         |
| [Select](../reference/arkui-cj/cj-button-picker-select.md) | Yes       | true         |
| [Slider](../reference/arkui-cj/cj-button-picker-slider.md) | Yes       | true         |
| [Span](../reference/arkui-cj/cj-text-input-span.md) | No       | false        |
| [Stepper](../reference/arkui-cj/cj-navigation-switching-stepper.md) | Yes       | true         |
| [StepperItem](../reference/arkui-cj/cj-navigation-switching-stepperitem.md) | Yes       | true         |
| [Text](../reference/arkui-cj/cj-text-input-text.md) | Yes       | false        |
| [TextArea](../reference/arkui-cj/cj-text-input-textarea.md) | No       | false         |
| [TextClock](../reference/arkui-cj/cj-information-display-textclock.md) | No       | false        |
| [TextInput](../reference/arkui-cj/cj-text-input-textinput.md) | Yes       | true         |
| [TextPicker](../reference/arkui-cj/cj-button-picker-textpicker.md) | Yes       | true         |
| [TextTimer](../reference/arkui-cj/cj-information-display-texttimer.md) | No       | false        |
| [Toggle](../reference/arkui-cj/cj-button-picker-toggle.md) | Yes       | true         |

Container component focus capabilities are as follows:

| Container Component                                     | Can Gain Focus | Default focusable Value |
| :---------------------------------------- | :------- | :------------ |
| [Badge](../reference/arkui-cj/cj-information-display-badge.md) | No     | false        |
| [Column](../reference/arkui-cj/cj-row-column-stack-column.md) | Yes     | true         |
| [Flex](../reference/arkui-cj/cj-row-column-stack-flex.md) | Yes     | true         |
| [GridCol](../reference/arkui-cj/cj-grid-layout-gridcol.md) | Yes     | true         |
| [GridRow](../reference/arkui-cj/cj-grid-layout-gridrow.md) | Yes     | true         |
| [Grid](../reference/arkui-cj/cj-scroll-swipe-grid.md) | Yes     | true         |
| [GridItem](../reference/arkui-cj/cj-scroll-swipe-griditem.md) | Yes     | true         |
| [List](../reference/arkui-cj/cj-scroll-swipe-list.md) | Yes     | true         |
| [ListItem](../reference/arkui-cj//cj-scroll-swipe-listitem.md) | Yes     | true         |
| [ListItemGroup](../reference/arkui-cj/cj-scroll-swipe-listgroup.md) | Yes     | true         |
| [Navigator](../reference/arkui-cj/cj-navigation-switching-navigation.md) | Yes     | true         |
| [Refresh](../reference/arkui-cj/cj-scroll-swipe-refresh.md) | Yes     | true        |
| [RelativeContainer](../reference/arkui-cj/cj-row-column-stack-relativecontainer.md) | No     | false         |
| [Row](../reference/arkui-cj/cj-row-column-stack-row.md) | Yes    | true         |
| [RowSplit](../reference/arkui-cj/cj-grid-layout-rowsplit.md) | Yes     | true         |
| [Scroll](../reference/arkui-cj/cj-scroll-swipe-scroll.md) | Yes     | true         |
| [SideBarContainer](../reference/arkui-cj/cj-grid-layout-sidebar.md) | Yes     | true         |
| [Stack](../reference/arkui-cj/cj-row-column-stack-stack.md) | Yes     | true         |
| [Swiper](../reference/arkui-cj/cj-scroll-swipe-swiper.md) | Yes     | true         |
| [Tabs](../reference/arkui-cj/cj-navigation-switching-tabs.md) | Yes     | true         |

Media component focus capabilities are as follows:

| Media Component                                     | Can Gain Focus | Default focusable Value |
| :---------------------------------------- | :------- | :------------ |
| [Video](../reference/arkui-cj/cj-image-video-video.md) | Yes     | true         |