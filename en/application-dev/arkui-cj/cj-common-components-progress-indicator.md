# Progress Bar (Progress)

Progress is a display component that shows the current progress of a target operation. For specific usage, please refer to [Progress](../reference/arkui-cj/cj-information-display-progress.md).

## Creating a Progress Bar

Progress is created by calling an interface with the following syntax:

```cangjie
Progress(value!: Float64, total!: Float64 = 100.0, progressType!: ProgressType = ProgressType.Linear)
```

Here, `value` sets the initial progress value, `total` sets the total length of the progress, and `ProgressType` sets the style of the ProgressType.

```cangjie
Progress(value: 24.0, total: 100.0, progressType: ProgressType.Linear) // Creates a linear progress bar with a total length of 100 and an initial progress value of 24
```

![create](figures/create.png)

## Setting Progress Bar Styles

Progress has 5 optional types, which can be set via `ProgressType`. The ProgressType styles include: `ProgressType.Linear` (linear style), `ProgressType.Ring` (ring style without scales), `ProgressType.ScaleRing` (ring style with scales), `ProgressType.Eclipse` (circular style), and `ProgressType.Capsule` (capsule style).

- Linear Style Progress Bar (default type)

  ```cangjie
  Progress(value: 20.0, total: 100.0, progressType: ProgressType.Linear)
      .width(200)
      .height(50)
  Progress(value: 20.0, total: 100.0, progressType: ProgressType.Linear)
      .width(50)
      .height(200)
  ```

  ![progress_linear](figures/progress_linear.png)

- Ring Style Progress Bar Without Scales

  ```cangjie
  // From left to right, Ring Progress Bar 1, default foreground color is blue gradient, default strokeWidth is 2.vp
  Progress(value: 40.0, total: 150.0, progressType: ProgressType.Ring)
      .width(100)
      .height(100)
  // From left to right, Ring Progress Bar 2
  Progress(value: 40.0, total: 150.0, progressType: ProgressType.Ring)
      .width(100)
      .height(100)
      .color(Color.Gray) // Sets the foreground color to gray
      .style(strokeWidth: 15.vp) // Sets the strokeWidth to 15.vp
  ```

  ![progress_ring](figures/progress_ring.png)

- Ring Style Progress Bar With Scales

  ```cangjie
  Progress(value: 20.0, total: 150.0, progressType: ProgressType.ScaleRing)
      .width(100)
      .height(100)
      .backgroundColor(Color.Black)
      .style(scaleCount: 20, scaleWidth: 5.vp) // Sets the total number of scales to 20 and scale width to 5.vp
  Progress(value: 20.0, total: 150.0, progressType: ProgressType.ScaleRing)
      .width(100)
      .height(100)
      .backgroundColor(Color.Black)
      .style(strokeWidth: 15.vp, scaleCount: 20, scaleWidth: 5.vp) // Sets the strokeWidth to 15.vp, total scales to 20, and scale width to 5.vp
  Progress(value: 20.0, total: 150.0, progressType: ProgressType.ScaleRing)
      .width(100)
      .height(100)
      .backgroundColor(Color.Black)
      .style(strokeWidth: 15.vp, scaleCount: 20, scaleWidth: 3.vp) // Sets the strokeWidth to 15.vp, total scales to 20, and scale width to 3.vp
  ```

  ![progress_scalering](figures/progress_scalering.png)

- Circular Style Progress Bar

  ```cangjie
  // From left to right, Circular Progress Bar 1, default foreground color is blue
  Progress(value: 10.0, total: 150.0, progressType: ProgressType.Eclipse)
      .width(100)
      .height(100)
  // From left to right, Circular Progress Bar 2, foreground color set to gray
  Progress(value: 20.0, total: 150.0, progressType: ProgressType.Eclipse)
      .color(Color.Gray)
      .width(100)
      .height(100)
  ```

  ![progress_circle](figures/progress_circle.png)

- Capsule Style Progress Bar

> **Note:**
>
> - The progress display effect at the rounded ends is the same as the `ProgressType.Eclipse` style.
>
> - The progress display effect in the middle segment is a rectangular bar, similar to the `ProgressType.Linear` style.
>
> - When the component height exceeds its width, it automatically adapts to a vertical display.

  ```cangjie
  Progress(value: 10.0, total: 150.0, progressType: ProgressType.Capsule)
      .width(100)
      .height(50)
  Progress(value: 20.0, total: 150.0, progressType: ProgressType.Capsule)
      .width(50)
      .height(100)
      .color(Color.Gray)
  Progress(value: 50.0, total: 150.0, progressType: ProgressType.Capsule)
      .width(50)
      .height(100)
      .color(Color.Blue)
      .backgroundColor(Color.Black)
  ```

  ![progress_captule](figures/progress_captule.png)

## Usage Example

Updating the current progress value, such as in an application installation progress bar, can be achieved by clicking a Button to increment `progressValue`. The `value` property assigns `progressValue` to the Progress component, which then triggers a refresh to update the current progress.

 <!-- run -->

```cangjie
package ohos_app_cangjie_entry
import kit.ArkUI.*
import ohos.arkui.state_macro_manage.*

@Entry
@Component
class EntryView {
    @State
    var progressValue: Float64 = 0.0 // Sets the initial progress value to 0
    func build() {
        Column() {
            Column() {
                Progress(value: 0.0, total: 100.0, progressType: ProgressType.Capsule)
                    .width(200)
                    .height(50)
                    .value(this.progressValue)
                Row()
                    .width(100.percent)
                    .height(5)
                Button("Progress +5").onClick ({
                    evt =>
                    this.progressValue += 5.0
                    if (this.progressValue > 100.0) {
                        this.progressValue = 0.0
                    }
                })
            }
        }
        .width(100.percent)
        .height(100.percent)
    }
}
```

![progress](figures/progress.gif)