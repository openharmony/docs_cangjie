# Tabs

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

When a page contains abundant information, tabs are used to help users focus on the currently displayed content by categorizing page content and improving space utilization. The [Tabs](../reference/arkui-cj/cj-navigation-switching-tabs.md) component enables quick switching between views within a single page, enhancing information retrieval efficiency while streamlining the amount of information users access at once.

## Basic Layout

The Tabs component consists of two parts: TabContent and TabBar. TabContent represents the content area, while TabBar serves as the navigation tab bar. The page structure is illustrated below, with layout variations based on navigation types: bottom navigation, top navigation, and side navigation, where the navigation bar is positioned at the bottom, top, or side respectively.

**Figure 1** Tabs Component Layout Schematic  

![tab-1](figures/tab-1.png)

> **Note:**  
> - The TabContent component does not support generic width properties; its width defaults to filling the parent Tabs component.  
> - The TabContent component does not support generic height properties; its height is determined by the parent Tabs component's height and the TabBar component's height.  

Tabs wrap TabContent in curly braces, as shown in Figure 2, where TabContent displays the corresponding content page.  

![tab-2](figures/tab-2.png)  

Each TabContent requires an associated tab, configured via its `tabBar` property. The example below demonstrates setting tab content for a TabContent component, where `tabBar` serves as the content tab.  

```cangjie  
 TabContent() {  
   Text('Home Content').fontSize(30)  
 }  
.tabBar('Home')  
```  

For multiple content sections, place them sequentially within Tabs.  

```cangjie  
Tabs() {  
  TabContent() {  
    Text('Home Content').fontSize(30)  
  }  
  .tabBar('Home')  

  TabContent() {  
    Text('Recommendations').fontSize(30)  
  }  
  .tabBar('Recommend')  

  TabContent() {  
    Text('Discover Content').fontSize(30)  
  }  
  .tabBar('Discover')  

  TabContent() {  
    Text('My Content').fontSize(30)  
  }  
  .tabBar("Mine")  
}  
```  

## Bottom Navigation  

Bottom navigation is the most common navigation pattern in applications. Positioned at the bottom of primary pages, it helps users understand the app's functional categories and corresponding content while facilitating one-handed operation. Typically serving as the main navigation, it organizes user-centric content by function, aligning with usage habits and simplifying transitions between modules.  

**Figure 3** Bottom Navigation Bar  

![tab-3](figures/tab-3.gif)  

The navigation bar position is set via Tabs' `barPosition` parameter. By default, the bar is at the top (`BarPosition.Start`). For bottom navigation, set `barPosition` to `BarPosition.End`.  

```cangjie  
Tabs(barPosition: BarPosition.End) {  
    // TabContent content, e.g., Home, Discover, Recommend, Mine  
    // ...  
}  
```  

## Top Navigation  

When content categories are numerous and users frequently switch between them, top navigation is often employed. This design further subdivides bottom navigation content, commonly seen in news apps (e.g., Follow, Video, Tech) or theme-based apps (e.g., Images, Videos, Fonts).  

**Figure 4** Top Navigation Bar  

![tab-4](figures/tab-4.gif)  

```cangjie  
Tabs(barPosition: BarPosition.Start) {  
    // TabContent content, e.g., Follow, Video, Games, Tech, Sports  
    // ...  
}  
```  

## Side Navigation  

Side navigation is less common and typically used in landscape interfaces. Aligned with left-to-right reading habits, the default side navigation bar is positioned on the left.  

**Figure 5** Side Navigation Bar  

![tab-5](figures/tab-5.png)  

To implement side navigation, set Tabs' `vertical` property to `true` (default is `false`, indicating vertical arrangement of content and navigation bars).  

```cangjie  
Tabs(barPosition: BarPosition.Start) {  
    // TabContent content, e.g., Home, Discover, Recommend, Mine  
    // ...  
}  
.vertical(true)  
```  

> **Note:**  
> - When `vertical` is `false`, the tabBar width defaults to full screen width; adjust via `barWidth`.  
> - When `vertical` is `true`, the tabBar height defaults to content height; adjust via `barHeight`.  

## Disabling Swipe Navigation  

By default, navigation bars support swipe switching. For multi-level categorization (e.g., combined bottom + top navigation), swiping conflicts may arise. In such cases, disable bottom navigation swiping to improve user experience.  

**Figure 6** Disabled Bottom Navigation Swiping  

![tab-6](figures/tab-6.gif)  

The `scrollable` property controls swipe switching (default: `true`). Set to `false` to disable.  

```cangjie  
Tabs(barPosition: BarPosition.End) {  
    TabContent() {  
        Column() {  
            Tabs() {  
                // Top navigation content  
                // ...  
            }  
        }  
        .backgroundColor(0XFF08A8F1)  
        .width(100.percent)  
    }  
    .tabBar("Home")  

    // Other TabContent, e.g., Discover, Recommend, Mine  
    // ...  
}  
.scrollable(false)  
```  

## Fixed Navigation Bar  

For fixed, non-expandable categories (e.g., bottom navigation with 3–5 tabs), use a fixed navigation bar. This non-scrollable layout evenly distributes tabBar width.  

**Figure 7** Fixed Navigation Bar  

![tab-7](figures/tab-7.gif)  

Tabs' `barMode` property controls scrollability (default: `BarMode.Fixed`).  

```cangjie  
Tabs(barPosition: BarPosition.End) {  
    // TabContent content, e.g., Home, Discover, Recommend, Mine  
    // ...  
}  
.barMode(BarMode.Fixed)  
```  

## Scrollable Navigation Bar  

Scrollable navigation bars suit top or side navigation with numerous categories exceeding screen width. Users can click or swipe to access hidden tabs.  

**Figure 8** Scrollable Navigation Bar  

![tab-8](figures/tab-8.gif)  

Set `barMode` to `BarMode.Scrollable` (default: `BarMode.Fixed`).  

```cangjie  
Tabs(barPosition: BarPosition.Start) {  
    // TabContent content, e.g., Home, Discover, Recommend, Mine  
    // ...  
}  
.barMode(BarMode.Scrollable)  
```  

## Custom Navigation Bar  

For bottom navigation as primary functional segmentation, combining text and icons enhances UX. Custom styling is required to distinguish active/inactive tabs.  

**Figure 9** Custom Navigation Bar  

![tab-9](figures/tab-9.png)  

By default, an underline indicates the active tab. Custom implementations must handle this distinction.  

Use `tabBar`'s `CustomBuilder` to pass custom function components. For example, `tabBuilder` accepts parameters like title, index, and image resources for active/inactive states, rendering styles based on `currentIndex` matching.  

```cangjie  
@State var currentIndex: Int32 = 0  

@Builder  
func tabBuilder(title: String, targetIndex: Int32, imgs: Array<AppResource>) {  
    Column(){  
        if (this.currentIndex != targetIndex) {  
            Image(imgs[0]).size(width: 25, height: 25)  
            Text(title).fontColor(0X1698CE)  
        } else {  
            Image(imgs[1]).size(width: 25, height: 25)  
            Text(title).fontColor(0X6B6B6B)  
        }  
    }  
    .width(100.percent)  
    .height(50)  
    .justifyContent(FlexAlign.Center)  
}  
```  

Pass the custom component via `tabBar`:  

```cangjie  
TabContent(){  
  Text("My Content").fontSize(30)  
}.tabBar({ =>  
  bind(this.tabBuilder, this)("Mine", 0, [@r(app.media.mine_normal), @r(app.media.mine_selected)])  
})  
```  

## Switching to Specific Tabs  

With custom navigation bars, default tab switching logic is disabled. Implement synchronization between content and tab changes via Tabs' `onChange` event, updating `currentIndex` on index changes.  

**Figure 10** Unlinked Content and Tabs  

![tab-10](figures/tab-10.gif)  

```cangjie  
package ohos_app_cangjie_entry  
import kit.ArkUI.*  
import ohos.arkui.state_macro_manage.*  
import std.collection.ArrayList  

@Entry  
@Component  
public class EntryView {  
    @State var currentIndex: Int32 = 2  

    @Builder  
    func tabBuilder(title: String, targetIndex: Int32) {  
        Column(){  
            Text(title)  
                .fontColor(  
                    if (this.currentIndex == targetIndex) {  
                        0X1698CE  
                    } else {  
                        0X6B6B6B  
                    })  
        }  
    }  

    func build() {  
        Column() {  
            Tabs(barPosition: BarPosition.End){  
                TabContent(){  
                    // ...  
                }.tabBar({ =>  
                    bind(this.tabBuilder, this)("Home", 0)  
                }).backgroundColor(Color.Green)  
                TabContent() {  
                    // ...  
                }.tabBar({ =>  
                    bind(this.tabBuilder, this)("Discover", 1)  
                }).backgroundColor(Color(0xFFFF00))  
                TabContent() {  
                    // ...  
                }.tabBar({ =>  
                    bind(this.tabBuilder, this)("Recommend", 2)  
                }).backgroundColor(0xFEC0CD)  
                TabContent() {  
                    // ...  
                }.tabBar({ =>  
                    bind(this.tabBuilder, this)("Mine", 3)  
                }).backgroundColor(Color.Blue)  
            }  
            .animationDuration(0.0)  
            .backgroundColor(0xF1F3F5)  
            .onChange({index =>  
                this.currentIndex = index  
            })  
        }.width(100.percent)  
    }  
}  
```  

**Figure 11** Linked Content and Tabs  

![tab-11](figures/tab-11.gif)  

For programmatic tab switching without swiping/clicking, pass `currentIndex` to Tabs' `index` parameter or use `TabsController`'s `changeIndex` method to navigate to specific TabContent.  

**Figure 12** Switching to Specified Tab  

![tab-12](figures/tab-12.gif)