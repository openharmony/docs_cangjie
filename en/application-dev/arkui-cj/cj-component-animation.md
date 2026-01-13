# Component Animation  

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

ArkUI provides components with general attribute animation and transition animation capabilities, while also offering default animation effects for certain components. For example, the sliding animation of [List](../reference/arkui-cj/cj-scroll-swipe-list.md) and the click animation of [Button](../reference/arkui-cj/cj-button-picker-button.md#button) are built-in default animation effects. Based on these default animations, developers can further customize the animation effects of child components within container components using attribute animation and transition animation.  

## Using Default Component Animations  

Default component animations offer the following functionalities:  

- **User Feedback**: For instance, when a user clicks a Button component, it turns gray by default, confirming the selection operation.  

- **Enhanced Aesthetics and Dynamism**: Improves the refinement and liveliness of the interface.  

- **Reduced Development Effort**: For example, list scrolling components come with built-in sliding animations, which developers can directly utilize.  

For more effects, refer to [Component Documentation](../reference/arkui-cj/cj-row-column-stack-flex.md).  

Sample code:  

<!-- run -->  

```cangjie  
package ohos_app_cangjie_entry  
import kit.ArkUI.*  
import ohos.arkui.state_macro_manage.*  

@Entry  
@Component  
class EntryView {  
    func build() {  
        Row {  
            Checkbox(name: 'checkbox1', group: "checkboxGroup")  
                .select(true)  
                .shape(CheckBoxShape.Circle)  
                .size(width: 50, height: 50)  
        }  
        .width(100.percent)  
        .height(100.percent)  
        .justifyContent(FlexAlign.Center)  
    }  
}  
```  

![animation](figures/componentAnimation1.gif)  

## Creating Customized Component Animations  

Some components support customizing the animation effects of child items through [Attribute Animation](./cj-attribute-animation-overview.md) and [Transition Animation](./cj-transition-overview.md), enabling tailored animation effects. For example, the [Scroll](../reference/arkui-cj/cj-scroll-swipe-scroll.md) component allows customization of the animation effects for each child component during scrolling.  

- **Dynamic Effects**: Achieve various effects by modifying the affine properties of each Scroll child component during scrolling or clicking operations.  

- **Custom Animation During Scrolling**: To customize animations during scrolling, monitor the scroll distance in the `onScroll` callback and calculate the affine properties for each component. Alternatively, define custom gestures to track positions and manually invoke `ScrollTo` to adjust the scroll position.  

- **Final Position Adjustment**: Fine-tune the final scroll position in the `onScrollStop` callback or gesture end callback.