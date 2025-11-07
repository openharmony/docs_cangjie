# Linear Layout (Row/Column)

## Overview

Linear Layout (LinearLayout) is the most commonly used layout in development, constructed through linear containers [Row](../reference/arkui-cj/cj-row-column-stack-row.md) and [Column](../reference/arkui-cj/cj-row-column-stack-column.md). As the foundation of other layouts, child elements in a linear layout are arranged sequentially along a linear direction (horizontal or vertical). The arrangement direction is determined by the selected container component: child elements in a Column container are arranged vertically, while those in a Row container are arranged horizontally. Developers can choose between Row or Column containers to create linear layouts based on different arrangement requirements.

**Figure 1** Illustration of Child Element Arrangement in Column Container

![arrangement-child-elements-column](figures/arrangement-child-elements-column.png)

**Figure 2** Illustration of Child Element Arrangement in Row Container

![arrangement-child-elements-row](figures/arrangement-child-elements-row.png)

## Basic Concepts

- **Layout Container**: A component container with layout capabilities that can host other elements as its children. The layout container calculates dimensions and arranges its child elements.

- **Layout Child Element**: Elements inside a layout container.

- **Main Axis**: The axis along the layout direction in a linear layout container, where child elements are arranged by default. For a Row container, the main axis is horizontal; for a Column container, it is vertical.

- **Cross Axis**: The axis perpendicular to the main axis. For a Row container, the cross axis is vertical; for a Column container, it is horizontal.

- **Spacing**: The spacing between child elements in the layout.

## Spacing Between Child Elements Along the Arrangement Direction

Within a layout container, the `space` property can be used to set the spacing between child elements along the arrangement direction, ensuring equal spacing between them.

### Spacing in Column Container Along the Arrangement Direction

**Figure 3** Spacing Diagram in Column Container Along the Arrangement Direction

![arrangement-direction-column](figures/arrangement-direction-column.png)

 <!-- run -->

```cangjie
package ohos_app_cangjie_entry
import kit.ArkUI.*
import ohos.arkui.state_macro_manage.*

@Entry
@Component
class EntryView {
    func build() {
        Column(space: 20) {
            Text('space: 20').fontSize(15).fontColor(Color.Gray).width(90.percent)
            Row().width(90.percent).height(50).backgroundColor(0xF5DEB3)
            Row().width(90.percent).height(50).backgroundColor(0xD2B48C)
            Row().width(90.percent).height(50).backgroundColor(0xF5DEB3)
        }.width(100.percent)
    }
}
```

![arrangement-direction-column01](figures/arrangement-direction-column01.PNG)

### Spacing in Row Container Along the Arrangement Direction

**Figure 4** Spacing Diagram in Row Container Along the Arrangement Direction

![arrangement-direction-row](figures/arrangement-direction-row.png)

 <!-- run -->

```cangjie
package ohos_app_cangjie_entry
import kit.ArkUI.*
import ohos.arkui.state_macro_manage.*

@Entry
@Component
class EntryView {
    func build() {
        Row(space: 35) {
            Text('space: 35').fontSize(15).fontColor(Color.Gray)
            Row().width(10.percent).height(150).backgroundColor(0xF5DEB3)
            Row().width(10.percent).height(150).backgroundColor(0xD2B48C)
            Row().width(10.percent).height(150).backgroundColor(0xF5DEB3)
        }.width(90.percent)
    }
}
```

![image01](figures/image01.PNG)

## Alignment of Child Elements Along the Cross Axis

Within a layout container, the `alignItems` property can be used to set the alignment of child elements along the cross axis (perpendicular to the arrangement direction). This behavior remains consistent across different screen sizes. For a vertical cross axis, the alignment is of type [VerticalAlign](../reference/arkui-cj/cj-common-types.md#enum-verticalalign); for a horizontal cross axis, it is of type [HorizontalAlign](../reference/arkui-cj/cj-common-types.md#enum-horizontalalign).

The `alignSelf` property controls the alignment of a single child element along the container's cross axis and takes precedence over `alignItems`. If `alignSelf` is set, it overrides `alignItems` for that specific child element.

### Horizontal Alignment of Child Elements in Column Container

**Figure 5** Horizontal Alignment Diagram of Child Elements in Column Container

![horizontal-arrangement-child-column](figures/horizontal-arrangement-child-column.png)

- **HorizontalAlign.Start**: Child elements are left-aligned horizontally.

     <!-- run -->

  ```cangjie
  package ohos_app_cangjie_entry
  import kit.ArkUI.*
  import ohos.arkui.state_macro_manage.*

  @Entry
  @Component
  class EntryView {
      func build() {
          Column() {
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xF5DEB3)
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xD2B48C)
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xF5DEB3)
          }.width(100.percent).alignItems(HorizontalAlign.Start).backgroundColor(0xF2F2F2)
      }
  }
  ```

  ![Column1](figures/Column1.PNG)

- **HorizontalAlign.Center**: Child elements are center-aligned horizontally.

     <!-- run -->

  ```cangjie
  package ohos_app_cangjie_entry
  import kit.ArkUI.*
  import ohos.arkui.state_macro_manage.*

  @Entry
  @Component
  class EntryView {
      func build() {
          Column() {
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xF5DEB3)
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xD2B48C)
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xF5DEB3)
          }.width(100.percent).alignItems(HorizontalAlign.Center).backgroundColor(0xF2F2F2)
      }
  }
  ```

  ![Column2](figures/Column2.PNG)

- **HorizontalAlign.End**: Child elements are right-aligned horizontally.

     <!-- run -->

  ```cangjie
  package ohos_app_cangjie_entry
  import kit.ArkUI.*
  import ohos.arkui.state_macro_manage.*

  @Entry
  @Component
  class EntryView {
      func build() {
          Column() {
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xF5DEB3)
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xD2B48C)
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xF5DEB3)
          }.width(100.percent).alignItems(HorizontalAlign.End).backgroundColor(0xF2F2F2)
      }
  }
  ```

  ![Column3](figures/Column3.PNG)

### Vertical Alignment of Child Elements in Row Container

**Figure 6** Vertical Alignment Diagram of Child Elements in Row Container

![horizontal-arrangement-child-row](figures/horizontal-arrangement-child-row.png)

- **VerticalAlign.Top**: Child elements are top-aligned vertically.

     <!-- run -->

  ```cangjie
  package ohos_app_cangjie_entry
  import kit.ArkUI.*
  import ohos.arkui.state_macro_manage.*

  @Entry
  @Component
  class EntryView {
      func build() {
          Row() {
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xF5DEB3)
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xD2B48C)
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xF5DEB3)
          }.width(100.percent).height(200).alignItems(VerticalAlign.Top).backgroundColor(0xF2F2F2)
      }
  }
  ```

  ![Column4](figures/Column4.PNG)

- **VerticalAlign.Center**: Child elements are center-aligned vertically.

     <!-- run -->

  ```cangjie
  package ohos_app_cangjie_entry
  import kit.ArkUI.*
  import ohos.arkui.state_macro_manage.*

  @Entry
  @Component
  class EntryView {
      func build() {
          Row() {
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xF5DEB3)
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xD2B48C)
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xF5DEB3)
          }.width(100.percent).height(200).alignItems(VerticalAlign.Center).backgroundColor(0xF2F2F2)
      }
  }
  ```
  
  ![Column5](figures/Column5.PNG)

- **VerticalAlign.Bottom**: Child elements are bottom-aligned vertically.

     <!-- run -->

  ```cangjie
  package ohos_app_cangjie_entry
  import kit.ArkUI.*
  import ohos.arkui.state_macro_manage.*

  @Entry
  @Component
  class EntryView {
      func build() {
          Row() {
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xF5DEB3)
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xD2B48C)
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xF5DEB3)
          }.width(100.percent).height(200).alignItems(VerticalAlign.Bottom).backgroundColor(0xF2F2F2)
      }
  }
  ```

  ![Column6](figures/Column6.PNG)

## Arrangement of Child Elements Along the Main Axis

Within a layout container, the `justifyContent` property can be used to set the arrangement of child elements along the main axis. Child elements can be aligned from the start of the main axis, the end of the main axis, or evenly distributed along the main axis.

### Vertical Arrangement of Child Elements in Column Container

**Figure 7** Vertical Arrangement Diagram of Child Elements in Column Container

![vertial-arrangement-child-column](figures/vertial-arrangement-child-column.png)

- **justifyContent(FlexAlign.Start)**: Elements are aligned at the start of the vertical axis, with the first element aligned to the top and subsequent elements aligned to the previous one.

     <!-- run -->

  ```cangjie
  package ohos_app_cangjie_entry
  import kit.ArkUI.*
  import ohos.arkui.state_macro_manage.*

  @Entry
  @Component
  class EntryView {
      func build() {
          Column() {
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xF5DEB3)
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xD2B48C)
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xF5DEB3)
          }.width(100.percent).height(300).backgroundColor(0xF2F2F2).justifyContent(FlexAlign.Start)
      }
  }
  ```

  ![Column7](figures/Column7.PNG)

- **justifyContent(FlexAlign.Center)**: Elements are center-aligned vertically, with equal distance from the first element to the top and the last element to the bottom.

     <!-- run -->

  ```cangjie
  package ohos_app_cangjie_entry
  import kit.ArkUI.*
  import ohos.arkui.state_macro_manage.*

  @Entry
  @Component
  class EntryView {
      func build() {
          Column() {
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xF5DEB3)
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xD2B48C)
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xF5DEB3)
          }.width(100.percent).height(300).backgroundColor(0xF2F2F2).justifyContent(FlexAlign.Center)
      }
  }
  ```

  ![Column8](figures/Column8.PNG)

- **justifyContent(FlexAlign.End)**: Elements are aligned at the end of the vertical axis, with the last element aligned to the bottom and other elements aligned to the next one.

     <!-- run -->

  ```cangjie
  package ohos_app_cangjie_entry
  import kit.ArkUI.*
  import ohos.arkui.state_macro_manage.*

  @Entry
  @Component
  class EntryView {
      func build() {
          Column() {
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xF5DEB3)
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xD2B48C)
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xF5DEB3)
          }.width(100.percent).height(300).backgroundColor(0xF2F2F2).justifyContent(FlexAlign.End)
      }
  }
  ```

  ![Column9](figures/Column9.PNG)

- **justifyContent(FlexAlign.SpaceBetween)**: Elements are evenly distributed along the vertical axis, with equal spacing between adjacent elements. The first element is aligned to the top, and the last element is aligned to the bottom.

     <!-- run -->

  ```cangjie
  package ohos_app_cangjie_entry
  import kit.ArkUI.*
  import ohos.arkui.state_macro_manage.*

  @Entry
  @Component
  class EntryView {
      func build() {
          Column() {
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xF5DEB3)
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xD2B48C)
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xF5DEB3)
          }.width(100.percent).height(300).backgroundColor(0xF2F2F2).justifyContent(FlexAlign.SpaceBetween)
      }
  }
  ```

  ![Column10](figures/Column10.PNG)

- **justifyContent(FlexAlign.SpaceAround)**: Elements are evenly distributed along the vertical axis, with equal spacing between adjacent elements. The distance from the first element to the top and the last element to the bottom is half the spacing between adjacent elements.

     <!-- run -->

  ```cangjie
  package ohos_app_cangjie_entry
  import kit.ArkUI.*
  import ohos.arkui.state_macro_manage.*

  @Entry
  @Component
  class EntryView {
      func build() {
          Column() {
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xF5DEB3)
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xD2B48C)
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xF5DEB3)
          }.width(100.percent).height(300).backgroundColor(0xF2F2F2).justifyContent(FlexAlign.SpaceAround)
      }
  }
  ```

  ![Column11](figures/Column11.PNG)

- **justifyContent(FlexAlign.SpaceEvenly)**: Elements are evenly distributed along the vertical axis, with equal spacing between adjacent elements, as well as between the first element and the top, and the last element and the bottom.

     <!-- run -->

  ```cangjie
  package ohos_app_cangjie_entry
  import kit.ArkUI.*
  import ohos.arkui.state_macro_manage.*

  @Entry
  @Component
  class EntryView {
      func build() {
          Column() {
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xF5DEB3)
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xD2B48C)
              Column() {
              }.width(80.percent).height(50).backgroundColor(0xF5DEB3)
          }.width(100.percent).height(300).backgroundColor(0xF2F2F2).justifyContent(FlexAlign.SpaceEvenly)
      }
  }
  ```

  ![Column12](figures/Column12.PNG)

### Horizontal Arrangement of Child Elements in Row Container

**Figure 8** Horizontal Arrangement Diagram of Child Elements in Row Container

![vertial-arrangement-child-row](figures/vertial-arrangement-child-row.png)

- **justifyContent(FlexAlign.Start)**: Elements are aligned at the start of the horizontal axis, with the first element aligned to the left and subsequent elements aligned to the previous one.

     <!-- run -->

  ```cangjie
  package ohos_app_cangjie_entry
  import kit.ArkUI.*
  import ohos.arkui.state_macro_manage.*

  @Entry
  @Component
  class EntryView {
      func build() {
          Row() {
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xF5DEB3)
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xD2B48C)
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xF5DEB3)
          }.width(100.percent).height(200).backgroundColor(0xF2F2F2).justifyContent(FlexAlign.Start)
      }
  }
  ```

  ![Column13](figures/Column13.PNG)

- **justifyContent(FlexAlign.Center)**: Elements are center-aligned horizontally, with equal distance from the first element to the left and the last element to the right.
    <!-- run -->
    
      ```cangjie
      package ohos_app_cangjie_entry
      import kit.ArkUI.*
      import ohos.arkui.state_macro_manage.*
    
      @Entry
      @Component
      class EntryView {
          func build() {
              Row() {
                  Column() {
                  }.width(20.percent).height(30).backgroundColor(0xF5DEB3)
                  Column() {
                  }.width(20.percent).height(30).backgroundColor(0xD2B48C)
                  Column() {
                  }.width(20.percent).height(30).backgroundColor(0xF5DEB3)
              }.width(100.percent).height(200).backgroundColor(0xF2F2F2).justifyContent(FlexAlign.Center)
          }
      }
      ```
    
      ![Column14](figures/Column14.PNG)

- `justifyContent(FlexAlign.End)`: Aligns elements to the end of the horizontal axis, with the last element aligned to the end of the row and other elements aligned to the subsequent one.

     <!-- run -->

  ```cangjie
  package ohos_app_cangjie_entry
  import kit.ArkUI.*
  import ohos.arkui.state_macro_manage.*

  @Entry
  @Component
  class EntryView {
      func build() {
          Row() {
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xF5DEB3)
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xD2B48C)
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xF5DEB3)
          }.width(100.percent).height(200).backgroundColor(0xF2F2F2).justifyContent(FlexAlign.End)
      }
  }
  ```

  ![Column15](figures/Column15.PNG)

- `justifyContent(FlexAlign.SpaceBetween)`: Distributes elements evenly along the horizontal axis, with equal spacing between adjacent elements. The first element is aligned to the start of the row, and the last element is aligned to the end.

     <!-- run -->

  ```cangjie
  package ohos_app_cangjie_entry
  import kit.ArkUI.*
  import ohos.arkui.state_macro_manage.*

  @Entry
  @Component
  class EntryView {
      func build() {
          Row() {
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xF5DEB3)
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xD2B48C)
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xF5DEB3)
          }.width(100.percent).height(200).backgroundColor(0xF2F2F2).justifyContent(FlexAlign.SpaceBetween)
      }
  }
  ```

  ![Column16](figures/Column16.PNG)

- `justifyContent(FlexAlign.SpaceAround)`: Distributes elements evenly along the horizontal axis, with equal spacing between adjacent elements. The spacing between the first element and the start of the row, as well as between the last element and the end of the row, is half the spacing between adjacent elements.

     <!-- run -->

  ```cangjie
  package ohos_app_cangjie_entry
  import kit.ArkUI.*
  import ohos.arkui.state_macro_manage.*

  @Entry
  @Component
  class EntryView {
      func build() {
          Row() {
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xF5DEB3)
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xD2B48C)
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xF5DEB3)
          }.width(100.percent).height(200).backgroundColor(0xF2F2F2).justifyContent(FlexAlign.SpaceAround)
      }
  }
  ```

  ![Column17](figures/Column17.PNG)

- `justifyContent(FlexAlign.SpaceEvenly)`: Distributes elements evenly along the horizontal axis, with equal spacing between adjacent elements, as well as between the first element and the start of the row, and the last element and the end of the row.

     <!-- run -->

  ```cangjie
  package ohos_app_cangjie_entry
  import kit.ArkUI.*
  import ohos.arkui.state_macro_manage.*

  @Entry
  @Component
  class EntryView {
      func build() {
          Row() {
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xF5DEB3)
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xD2B48C)
              Column() {
              }.width(20.percent).height(30).backgroundColor(0xF5DEB3)
          }.width(100.percent).height(200).backgroundColor(0xF2F2F2).justifyContent(FlexAlign.SpaceEvenly)
      }
  }
  ```
        
  ![Column18](figures/Column18.PNG)

## Adaptive Stretching

In linear layouts, the [Blank](../reference/arkui-cj/cj-blank-divider-blank.md) component is commonly used to automatically fill blank space along the main axis of the container, achieving an adaptive stretching effect. When Row and Column serve as containers, simply setting their width and height as percentages will produce adaptive effects as the screen dimensions change.

<!-- run -->

```cangjie
package ohos_app_cangjie_entry
import kit.ArkUI.*
import ohos.arkui.state_macro_manage.*

@Entry
@Component
class EntryView {
    func build() {
        Column(){
            Row() {
                Text('Bluetooth').fontSize(18)
                Blank()
                Toggle(ToggleType.Switch,isOn: true)
            }.backgroundColor(0xFFFFFF).borderRadius(15).padding(left:12).width(100.percent)
        }.backgroundColor(0xEFEFEF).padding(20).width(100.percent)
    }
}
```

**Figure 9** Vertical Screen with Adaptive Stretching

![Column19](figures/Column19.PNG)

**Figure 10** Horizontal Screen with Adaptive Stretching

![Column20](figures/Column20.png)

## Adaptive Scaling

Adaptive scaling refers to child elements automatically adjusting their dimensions according to preset proportions as the container size changes, accommodating devices of various sizes. In linear layouts, the following two methods can be used to achieve adaptive scaling.

- When the parent container's dimensions are fixed, use the `layoutWeight` property to set the weights of child elements and their siblings along the main axis, ignoring the elements' own size settings. This ensures they adaptively fill the remaining space on devices of any size.

    <!-- run -->

  ```cangjie
  package ohos_app_cangjie_entry
  import kit.ArkUI.*
  import ohos.arkui.state_macro_manage.*

  @Entry
  @Component
  class EntryView {
      func build() {
          Column() {
              Text('1:2:3').width(100.percent)
              Row() {
                  Column() {
                      Text('layoutWeight(1)').textAlign(TextAlign.Center)
                  }
                  .layoutWeight(1)
                  .backgroundColor(0xF5DEB3)
                  .height(100.percent)
                  Column() {
                      Text('layoutWeight(2)').textAlign(TextAlign.Center)
                  }
                  .layoutWeight(2)
                  .backgroundColor(0xD2B48C)
                  .height(100.percent)
                  Column() {
                      Text('layoutWeight(3)').textAlign(TextAlign.Center)
                  }
                  .layoutWeight(3)
                  .backgroundColor(0xF5DEB3)
                  .height(100.percent)
              }
              .backgroundColor(0xffd306)
              .height(30.percent)
              Text('2:5:3').width(100.percent)
              Row() {
                  Column() {
                      Text('layoutWeight(2)').textAlign(TextAlign.Center)
                  }
                  .layoutWeight(2)
                  .backgroundColor(0xF5DEB3)
                  .height(100.percent)
                  Column() {
                      Text('layoutWeight(5)').textAlign(TextAlign.Center)
                  }
                  .layoutWeight(5)
                  .backgroundColor(0xD2B48C)
                  .height(100.percent)
                  Column() {
                      Text('layoutWeight(3)').textAlign(TextAlign.Center)
                  }
                  .layoutWeight(3)
                  .backgroundColor(0xF5DEB3)
                  .height(100.percent)
              }
              .backgroundColor(0xffd306)
              .height(30.percent)
          }
      }
  }
  ```

  **Figure 11** Horizontal Screen with Custom Scaling Using `layoutWeight`

  ![Column21](figures/Column21.png)

  **Figure 12** Vertical Screen with Custom Scaling Using `layoutWeight`

  ![Column22](figures/Column22.png)

- When the parent container's dimensions are fixed, use percentages to set the width of child elements and their siblings, ensuring they maintain a fixed adaptive proportion on devices of any size.

    <!-- run -->

  ```cangjie
  package ohos_app_cangjie_entry
  import kit.ArkUI.*
  import ohos.arkui.state_macro_manage.*

  @Entry
  @Component
  class EntryView {
      func build() {
          Column() {
              Row() {
                  Column() {
                      Text('left width 20%').textAlign(TextAlign.Center)
                  }
                  .width(20.percent)
                  .backgroundColor(0xF5DEB3)
                  .height(100.percent)
                  Column() {
                      Text('center width 50%').textAlign(TextAlign.Center)
                  }
                  .width(50.percent)
                  .backgroundColor(0xD2B48C)
                  .height(100.percent)
                  Column() {
                      Text('right width 30%').textAlign(TextAlign.Center)
                  }
                  .width(30.percent)
                  .backgroundColor(0xF5DEB3)
                  .height(100.percent)
              }
              .backgroundColor(0xffd306)
              .height(30.percent)
          }
      }
  }
  ```

  **Figure 13** Horizontal Screen with Custom Scaling Using Percentages

  ![Column23](figures/Column23.png)

  **Figure 14** Vertical Screen with Custom Scaling Using Percentages

  ![Column24](figures/Column24.png)

## Adaptive Extension

Adaptive extension refers to scenarios where content exceeds the screen size and cannot be fully displayed on devices of different dimensions. In such cases, scrollbars can be used to navigate the content. This method is suitable for linear layouts where content cannot be displayed on a single screen. Typically, there are two implementation approaches:

- [Adding Scrollbars to List](cj-layout-development-create-list.md): When a List contains too many items to fit on one screen, each item can be placed in separate components and displayed via scrollbars. The `scrollBar` property can be used to set the scrollbar's persistent state.

- Using the Scroll Component: In linear layouts, developers can arrange content vertically or horizontally. When content cannot be fully displayed on one screen, a Scroll component can wrap the Column or Row components to create a scrollable linear layout.

  Vertical Layout Using Scroll Component:

    <!-- run -->

  ```cangjie
  package ohos_app_cangjie_entry
  import kit.ArkUI.*
  import ohos.arkui.state_macro_manage.*

  @Entry
  @Component
  class EntryView {
      let scroller: Scroller = Scroller()
      private var arr: Array<Int64> = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
      func build() {
          Scroll(this.scroller) {
              Column() {
                  ForEach(this.arr,itemGeneratorFunc: {
                      item: Int64, idx: Int64 => Text(item.toString())
                          .width(90.percent)
                          .height(150)
                          .backgroundColor(0xFFFFFF)
                          .borderRadius(15)
                          .fontSize(16)
                          .textAlign(TextAlign.Center)
                          .margin(top: 10)
                      },
                      keyGeneratorFunc: {item: Int64, idx: Int64 => idx.toString()}
                  )
              }.width(100.percent)
          }
          .backgroundColor(0xDCDCDC)
          .scrollable(ScrollDirection.Vertical) // Scroll direction is vertical
          .scrollBar(BarState.On) // Scrollbar is always visible
          .scrollBarColor(Color.Gray) // Scrollbar color
          .scrollBarWidth(8.vp) // Scrollbar width
      }
  }
  ```

  ![Column25](figures/Column25.gif)

  Horizontal Layout Using Scroll Component:

    <!-- run -->

  ```cangjie
  package ohos_app_cangjie_entry
  import kit.ArkUI.*
  import ohos.arkui.state_macro_manage.*

  @Entry
  @Component
  class EntryView {
      let scroller: Scroller = Scroller()
      private var arr: Array<Int64> = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
      func build() {
          Scroll(this.scroller) {
              Row() {
                  ForEach(this.arr,itemGeneratorFunc: {
                      item: Int64, idx: Int64 =>
                      Text(item.toString())
                          .width(150)
                          .height(90.percent)
                          .backgroundColor(0xFFFFFF)
                          .borderRadius(15)
                          .fontSize(16)
                          .textAlign(TextAlign.Center)
                          .margin(left: 10)
                      }
                  )
              }.height(100.percent)
          }
          .backgroundColor(0xDCDCDC)
          .scrollable(ScrollDirection.Horizontal) // Scroll direction is horizontal
          .scrollBar(BarState.On) // Scrollbar is always visible
          .scrollBarColor(Color.Gray) // Scrollbar color
          .scrollBarWidth(8.vp) // Scrollbar width
      }
  }
  ```

  ![Column26](figures/Column26.gif)