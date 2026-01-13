# Animation Transitions

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

In addition to running animations, UI interfaces also serve the function of real-time interaction with users. When user behavior changes based on intent, the UI interface should respond immediately. For example, if a user swipes up to exit during the app launch process, the launch animation should immediately transition to the exit animation rather than waiting for the launch animation to complete before exiting, thereby reducing user wait time. For scenarios like desktop page-flipping animations triggered from touch-down to touch-up, the initial speed of the post-touch-up animation should inherit the gesture speed to avoid a sense of discontinuity or pause due to mismatched velocities. To address these scenarios, the system provides seamless transition capabilities between animations and between gestures and animations, ensuring smooth transitions across various use cases while minimizing development complexity.

Assume there is an ongoing animation for a particular animatable property. When UI-side behavior changes the target value of this property, developers only need to modify the property value within the [animateTo](../reference/arkui-cj/cj-apis-uicontext-uicontext.md#func-animateto) animation closure or change the property value affected by the [animation](../reference/arkui-cj/cj-animation-animation.md#func-animationanimateparam) interface to trigger a new animation. The system will automatically transition from the previous animation to the current one, allowing developers to focus solely on implementing the single animation instance.

The following example demonstrates this. Clicking the "Click" button changes the scale property of the red square. When clicking rapidly in succession, the target value of the scale property changes continuously, and the current animation smoothly transitions toward the new target value.

 <!--run-->

```cangjie
package ohos_app_cangjie_entry

import kit.ArkUI.*
import ohos.arkui.state_macro_manage.*

@Observed
class SetSlt {
    @Publish var isAnimation: Bool = true
    public func set() {
        this.isAnimation = !this.isAnimation
    }

    public func getScale(): Float32 {
        if (this.isAnimation){
            return 2.0
        }
        return 1.0
    }
}

@Entry
@Component
class EntryView {
    @State var SetAnimation: SetSlt = SetSlt()

    func build() {
        Column() {
            Text('ArkUI')
                .fontWeight(FontWeight.Bold)
                .fontSize(12)
                .fontColor(Color.White)
                .textAlign(TextAlign.Center)
                .borderRadius(10)
                .backgroundColor(0xf56c6c)
                .width(100)
                .height(100)
                .scale(x: this.SetAnimation.getScale(), y: this.SetAnimation.getScale())
                .animation(AnimateParam(curve: Curve.Ease))
            Button('Click')
                .margin(top: 200)
                .onClick({evt =>
                    this.SetAnimation.set()
                })
        }
        .width(100.percent)
        .height(100.percent)
        .justifyContent(FlexAlign.Center)
    }
}
```

![animation1](./figures/animation1.gif)

## Gesture-to-Animation Transitions

In scenarios involving gestures like swiping, pinching, or rotating, property changes are typically triggered during touch-down-to-touch-up interactions. After touch-up, these properties often continue to change until reaching their target values.

The initial velocity of property changes during the post-touch-up phase should match the velocity immediately before touch-up. If the property change velocity starts from zero after touch-up, it would resemble a moving car slamming its brakes—a jarring visual effect neither users nor developers desire.

For animations using the [springMotion](../reference/arkui-cj/cj-apis-curves.md#static-func-springmotionfloat32-float32-float32) curve, the post-touch-up animation automatically inherits the velocity from the touch-down phase, starting from the current position of the touch-down animation and moving toward the specified target value.

The following code example demonstrates a ball following touch movement.

 <!--run-->

```cangjie
package ohos_app_cangjie_entry

import kit.ArkUI.*
import ohos.arkui.state_macro_manage.*

@Entry
@Component
class EntryView {
    @State var positionX: Float64 = 100.0
    @State var positionY: Float64 = 100.0
    var diameter: Float64 = 50.0

    func build() {
        Column() {
            Row() {
                Circle(width: this.diameter, height: this.diameter)
                    .fill(Color.Blue)
                    .position(x: this.positionX, y: this.positionY)
                    .animation(AnimateParam(curve: Curve.EaseInOut))
                    .onTouch({ event: TouchEvent =>
                    if (event.eventType == TouchType.Move) {
                        this.positionX = event.touches[0].screenX - this.diameter / 2.0
                        this.positionY = event.touches[0].screenY - this.diameter / 2.0
                    } else if (event.eventType == TouchType.Up) {
                        this.positionX = 100.0
                        this.positionY = 100.0
                    }
                })
            }
            .width(100.percent)
            .height(80.percent)
            .clip(true) // If the ball exceeds parent component bounds, make it invisible
            .backgroundColor(0xFEA400)

            Flex(direction: FlexDirection.Row,justifyContent: FlexAlign.Center, alignItems: ItemAlign.Start) {
                Text("Drag the ball").fontSize(16)
            }
            .width(100.percent)

            Row() {
                Text('Position: [x: ${Int64(this.positionX)} y: ${Int64(this.positionY)}]').fontSize(16)
            }
            .padding(10)
            .width(100.percent)
        }
        .width(100.percent)
        .height(100.percent)
    }
}
```

![animation2](./figures/animation2.gif)