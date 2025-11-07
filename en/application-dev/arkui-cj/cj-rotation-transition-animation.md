# Rotation Screen Animation

Rotation screen animations are primarily divided into two categories: [Layout Transition Rotation Animation](#layout-transition-rotation-animation) and [Opacity Transition Rotation Animation](#opacity-transition-rotation-animation), designed to achieve natural transitions when the screen display orientation changes. The layout transition rotation animation is relatively simple to implement—for example, configuring auto-rotation in `module.json5` (or setting the window display orientation) suffices. In contrast, the opacity transition rotation animation requires preparing two sets of views in addition to the `module.json5` configuration. During screen rotation, the disappearing view gradually fades out while the newly appearing view fades in, creating a smooth visual experience.

## Layout Transition Rotation Animation

The layout transition rotation animation is designed to synchronize the window and application view rotation during screen orientation changes, providing size and position transition effects. This type of rotation animation is system-default and developer-friendly. When the screen orientation changes, the system generates a window rotation animation and automatically adjusts the window size to match the rotated dimensions. During this process, the window notifies the corresponding application to re-layout according to the new window size, producing a layout animation with parameters identical to the window rotation animation.

Switching the screen orientation achieves the layout transition rotation animation effect.

 <!--run-->

```cangjie
package ohos_app_cangjie_entry

import kit.ArkUI.*
import ohos.arkui.state_macro_manage.*
import ohos.resource_manager.*

@Entry
@Component
class EntryView{
    func build(){
        Column(){
            Image(@r(app.media.foreground))
                .position(x: 0,y: 0)
                .size(width: 100,height: 100)
                .id('image1')
                .backgroundColor(Color.Blue)
        }
    }
}
```

Add `"orientation": "auto_rotation"` to the `abilities` list in the project's `module.json5` file.

```json
"orientation": "auto_rotation",
```

The layout transition rotation animation applies size and position transitions to the synchronously rotating window and application view.

![Alt text](./figures/rotation-transition1.gif)

## Opacity Transition Rotation Animation

The opacity transition rotation animation activates when the screen display orientation changes. During the window rotation animation, it adds a default opacity transition to newly added or removed components, enabling graceful appearance and disappearance of components. This functionality listens for window rotation events and switches component view effects accordingly. If the root nodes of the disappearing and newly appearing views have no transition effects set, a default opacity transition (i.e., [`TransitionEffect`](../reference/arkui-cj/cj-animation-transition.md#class-transitioneffect).OPACITY) is automatically applied, creating fade-out and fade-in effects.

 <!-- run -example1 -->

```cangjie
package ohos_app_cangjie_entry

import kit.ArkUI.*
import ohos.arkui.state_macro_manage.*
import ohos.resource_manager.*
import ohos.display.*
import ohos.display.{Orientation as DisplayOrientation}

func matchor(orientation: DisplayOrientation): String {
    match(orientation){
        case Landscape => "Landscape"
        case Portrait => "Portrait"
        case LandscapeInverted => "LandscapeInverted"
        case PortraitInverted => "PortraitInverted"
        case _ => "FollowDesktop"
    }
}

@Entry
@Component
class EntryView{
    // Get the screen display orientation by listening to the window's windowsSizeChange event
    @StorageLink["orientation"] var orientation: DisplayOrientation  = DisplayOrientation.Portrait

    func build(){
        Stack() {
            if(matchor(orientation) == "Portrait"|| matchor(orientation) == "PortraitInverted"){
                Image(@r(app.media.startIcon))
                    .size(width: 100, height: 100 )
                    .id('image1')
                  // Developers can also manually set the TransitionEffect.OPACITY transition effect to achieve opacity changes in the rotation animation
//                   .transition(TransitionEffect.OPACITY)
            }else{
                Image(@r(app.media.startIcon))
                    .position(x: 0, y: 0 )
                    .size( width: 200, height: 200)
                    .id('image2')
                    // Developers can also manually set the TransitionEffect.OPACITY transition effect to achieve opacity changes in the rotation animation
//                    .transition(TransitionEffect.OPACITY)
            }
        }.backgroundColor(Color.White).size(width: 100.percent, height: 100.percent)
    }
}
```

Listen to the synchronous `windowsSizeChange` event for window rotation to implement view switching. For example, add processing logic in the `onWindowStageCreate` method of the `main_ability.cj` file to obtain the screen display orientation.

Add `"orientation": "auto_rotation"` to the `abilities` list in the project's `module.json5` file.

```json
"orientation": "auto_rotation",
```

The opacity transition rotation animation applies size and position transitions to the window while simultaneously transitioning the application view. It fades out the disappearing view and fades in the newly appearing view.

![rotation-opacity](figures/rotation-opacity.gif)