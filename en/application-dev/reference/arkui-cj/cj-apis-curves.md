# ohos.curves (Interpolation Calculation)

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

Provides interpolator functions such as initialization, cubic Bézier curves, and spring curves.

## Import Module

```cangjie
import kit.ArkUI.*
```

## class Curves

```cangjie
public class Curves {}
```

**Function:** Contains interpolator functions such as initialization, cubic Bézier curves, and spring curves.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

### static func cubicBezierCurve(Float32, Float32, Float32, Float32)

```cangjie
public static func cubicBezierCurve(x1: Float32, y1: Float32, x2: Float32, y2: Float32): ICurve
```

**Function:** Constructs a cubic Bézier curve object, ensuring the curve values are between 0 and 1.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type    | Required | Default | Description |
|:----------|:--------|:---------|:--------|:------------|
| x1        | Float32 | Yes      | -       | Determines the x-coordinate of the first point of the Bézier curve.<br>Range: [0, 1]<br>**Note:**<br>Values less than 0 are treated as 0; values greater than 1 are treated as 1. |
| y1        | Float32 | Yes      | -       | Determines the y-coordinate of the first point of the Bézier curve.<br>Range: (-∞, +∞). |
| x2        | Float32 | Yes      | -       | Determines the x-coordinate of the second point of the Bézier curve.<br>Range: [0, 1].<br>**Note:**<br>Values less than 0 are treated as 0; values greater than 1 are treated as 1. |
| y2        | Float32 | Yes      | -       | Determines the y-coordinate of the second point of the Bézier curve.<br>Range: (-∞, +∞). |

**Return Value:**

| Type           | Description |
|:---------------|:------------|
| [ICurve](#class-icurve) | Returns the interpolator object of the curve. |

### static func customCurve((Float32) -> Float32)

```cangjie
public static func customCurve(interpolate: (Float32) -> Float32): ICurve
```

**Function:** Creates a custom curve.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter   | Type              | Required | Default | Description |
|:------------|:------------------|:---------|:--------|:------------|
| interpolate | (Float32) -> Float32 | Yes      | -       | User-defined interpolation callback function.<br>The input x value for interpolation at the start of the animation.<br>Range: [0, 1].<br>The return value is the y value of the curve.<br>Range: [0, 1].<br>**Note:**<br>When fraction equals 0, a return value of 0 corresponds to the animation start point. A non-zero return value will cause a jump effect at the start. When fraction equals 1, a return value of 1 corresponds to the animation end point. A non-1 return value will cause the animation's final value to deviate from the state variable's value, resulting in a jump effect to the state variable's value. |

**Return Value:**

| Type           | Description |
|:---------------|:------------|
| [ICurve](#class-icurve) | Returns the interpolator object of the curve. |

### static func initCurve(Curve)

```cangjie
public static func initCurve(curve!: Curve = Curve.Linear): ICurve
```

**Function:** Initializes an interpolation curve function, creating an interpolation curve object based on the input parameters.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type                          | Required | Default      | Description |
|:----------|:------------------------------|:---------|:-------------|:------------|
| curve     | [Curve](./cj-common-types.md#enum-curve) | No       | Curve.Linear | **Named parameter.** The type of curve. |

**Return Value:**

| Type           | Description |
|:---------------|:------------|
| [ICurve](#class-icurve) | Returns the interpolator object of the curve. |

### static func interpolatingSpring(Float32, Float32, Float32, Float32)

```cangjie
public static func interpolatingSpring(velocity: Float32, mass: Float32, stiffness: Float32, damping: Float32): ICurve
```

**Function:** Constructs an interpolator spring curve object, generating an animation curve from 0 to 1. The actual animation value is calculated through interpolation based on the curve. The animation duration is determined by the curve parameters and is not controlled by the duration parameter in `animation` or `animateTo`.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter  | Type    | Required | Default | Description |
|:-----------|:--------|:---------|:--------|:------------|
| velocity   | Float32 | Yes      | -       | Initial velocity. A parameter representing external influences on the spring animation, ensuring a smooth transition from the previous motion state to the spring animation. This velocity is normalized, equal to the actual velocity at the start of the animation divided by the change in the animation property.<br>Range: (-∞, +∞). |
| mass       | Float32 | Yes      | -       | Mass. The object subjected to forces in the spring system, affecting the system's inertia. Larger mass results in greater oscillation amplitude and slower return to equilibrium.<br>Range: (0, +∞).<br>**Note:**<br>Values less than or equal to 0 are treated as 1. |
| stiffness  | Float32 | Yes      | -       | Stiffness. Represents the object's resistance to deformation under applied force. Higher stiffness results in faster return to equilibrium.<br>**Note:**<br>Values less than or equal to 0 are treated as 1. |
| damping    | Float32 | Yes      | -       | Damping. Describes the oscillation and decay of the system after disturbance. Higher damping results in fewer oscillations and smaller amplitudes.<br>Range: (0, +∞).<br>**Note:**<br>Values less than or equal to 0 are treated as 1. |

**Return Value:**

| Type           | Description |
|:---------------|:------------|
| [ICurve](#class-icurve) | The interpolator object of the curve.<br>**Note:** The spring animation curve is a physical curve. The duration parameter in [animation](./cj-animation-animation.md), [animateTo](./cj-apis-uicontext-uicontext.md#func-animatetoanimateparam-voidcallback), and [pageTransition](./cj-animation-pagetransition.md) does not take effect. The animation duration depends on the `interpolatingSpring` curve parameters. Time cannot be normalized, so interpolation cannot be obtained via the [interpolate](#func-interpolatefloat32) function of this curve. |

### static func responsiveSpringMotion(Float32, Float32, Float32)

```cangjie
public static func responsiveSpringMotion(response!: Float32 = 0.15, dampingFraction!: Float32 = 0.86,
    overlapDuration!: Float32 = 0.25): ICurve
```

**Function:** Creates a responsive spring animation curve. It is a special case of [springMotion](#static-func-springmotionfloat32-float32-float32) with different default parameters and can be used alongside `springMotion`.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter       | Type    | Required | Default | Description |
|:----------------|:--------|:---------|:--------|:------------|
| response        | Float32 | No       | 0.15    | **Named parameter.** Same as `response` in `springMotion`.<br>Unit: seconds.<br>Range: (0, +∞).<br>**Note:**<br>Values less than or equal to 0 are treated as the default value 0.15. |
| dampingFraction | Float32 | No       | 0.86    | **Named parameter.** Same as `dampingFraction` in `springMotion`.<br>Unit: seconds.<br>Range: (0, +∞).<br>**Note:**<br>Values less than or equal to 0 are treated as the default value 0.86. |
| overlapDuration | Float32 | No       | 0.25    | **Named parameter.** Same as `overlapDuration` in `springMotion`.<br>Unit: seconds.<br>Range: (0, +∞).<br>**Note:**<br>The responsive spring animation curve is a special case of `springMotion` with different default parameters. For custom spring curves, it is recommended to use `springMotion`. For hand-following animations, it is recommended to use the default parameters of the responsive spring animation curve.<br>The duration parameter in [animation](./cj-animation-animation.md), [animateTo](./cj-apis-uicontext-uicontext.md#func-animatetoanimateparam-voidcallback), and [pageTransition](./cj-animation-pagetransition.md) does not take effect. The animation duration depends on the `responsiveSpringMotion` curve parameters and previous velocity. Interpolation cannot be obtained via the [interpolate](#func-interpolatefloat32) function of this curve. |

**Return Value:**

| Type           | Description |
|:---------------|:------------|
| [ICurve](#class-icurve) | The curve object.<br>**Note:**<br>1. The responsive spring animation curve is a special case of `springMotion` with different default parameters. For custom spring curves, it is recommended to use `springMotion`. For hand-following animations, it is recommended to use the default parameters of the responsive spring animation curve.<br>2. The duration parameter in [animation](./cj-animation-animation.md), [animateTo](./cj-apis-uicontext-uicontext.md#func-animatetoanimateparam-voidcallback), and [pageTransition](./cj-animation-pagetransition.md) does not take effect. The animation duration depends on the `responsiveSpringMotion` curve parameters and previous velocity. Interpolation cannot be obtained via the [interpolate](#func-interpolatefloat32) function of this curve. |

### static func springCurve(Float32, Float32, Float32, Float32)

```cangjie
public static func springCurve(velocity: Float32, mass: Float32, stiffness: Float32, damping: Float32): ICurve
```

**Function:** Creates a spring curve object. The curve shape is determined by the spring parameters, and the animation duration is controlled by the duration parameter in `animation` and `animateTo`.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter  | Type    | Required | Default | Description |
|:-----------|:--------|:---------|:--------|:------------|
| velocity   | Float32 | Yes      | -       | Initial velocity. Represents external influences on the spring animation, ensuring a smooth transition from the previous motion state to the spring animation. This velocity is normalized, equal to the actual velocity at the start of the animation divided by the change in the animation property.<br>Range: (-∞, +∞). |
| mass       | Float32 | Yes      | -       | Mass. The object subjected to forces in the spring system, affecting the system's inertia. Larger mass results in greater oscillation amplitude and slower return to equilibrium.<br>Range: (0, +∞).<br>**Note:**<br>Values less than or equal to 0 are treated as 1. |
| stiffness  | Float32 | Yes      | -       | Stiffness. Represents the object's resistance to deformation under applied force. Higher stiffness results in faster return to equilibrium.<br>Range: (0, +∞).<br>**Note:**<br>Values less than or equal to 0 are treated as 1. |
| damping    | Float32 | Yes      | -       | Damping. Describes the oscillation and decay of the system after disturbance. Higher damping results in fewer oscillations and smaller amplitudes.<br>Range: (0, +∞).<br>**Note:**<br>Values less than or equal to 0 are treated as 1. |

**Return Value:**

| Type           | Description |
|:---------------|:------------|
| [ICurve](#class-icurve) | Returns the interpolator object of the curve. |

### static func springMotion(Float32, Float32, Float32)

```cangjie
public static func springMotion(response!: Float32 = 0.55, dampingFraction!: Float32 = 0.825,
    overlapDuration!: Float32 = 0.0): ICurve
```

**Function:** Creates a spring animation curve object. If multiple spring animations are applied to the same property of the same object, each animation will replace the previous one and inherit its velocity.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter       | Type    | Required | Default | Description |
|:----------------|:--------|:---------|:--------|:------------|
| response        | Float32 | No       | 0.55    | **Named parameter.** The natural oscillation period of the spring, determining the speed of returning to equilibrium.<br>Unit: seconds.<br>Range: (0, +∞).<br>**Note:**<br>Values less than or equal to 0 are treated as the default value 0.55. |
| dampingFraction | Float32 | No       | 0.825   | **Named parameter.** Damping coefficient.<br>0 indicates no damping, resulting in continuous oscillation;<br>Values greater than 0 and less than 1 indicate underdamping, causing overshooting;<br>1 indicates critical damping;<br>Values greater than 1 indicate overdamping, gradually approaching the target value.<br>Unit: seconds.<br>Range: (0, +∞).<br>**Note:**<br>Values less than or equal to 0 are treated as the default value 0.825. |
| overlapDuration | Float32 | No       | 0.0     | **Named parameter.** The transition duration for spring animation inheritance. When animations are inherited, if the `response` parameters of consecutive spring animations differ, the `response` parameter will smoothly transition over the `overlapDuration` time.<br>Unit: seconds.<br>Range: (0, +∞).<br>**Note:**<br>Values less than 0 are treated as the default value 0.<br>The spring animation curve is a physical curve. The duration parameter in [animation](./cj-animation-animation.md), [animateTo](./cj-apis-uicontext-uicontext.md#func-animatetoanimateparam-voidcallback), and [pageTransition](./cj-animation-pagetransition.md) does not take effect. The animation duration depends on the `springMotion` curve parameters and previous velocity. Time cannot be normalized, so interpolation cannot be obtained via the [interpolate](#func-interpolatefloat32) function of this curve. |

**Return Value:**

| Type           | Description |
|:---------------|:------------|
| [ICurve](#class-icurve) | The curve object.<br>**Note:** The spring animation curve is a physical curve. The duration parameter in [animation](./cj-animation-animation.md), [animateTo](./cj-apis-uicontext-uicontext.md#func-animatetoanimateparam-voidcallback), and [pageTransition](./cj-animation-pagetransition.md) does not take effect. The animation duration depends on the `springMotion` curve parameters and previous velocity. Time cannot be normalized, so interpolation cannot be obtained via the [interpolate](#func-interpolatefloat32) function of this curve. |

### static func stepsCurve(Int32, Bool)

```cangjie
public static func stepsCurve(count: Int32, end: Bool): ICurve
```

**Function:** Creates a step curve object.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type  | Required | Default | Description |
|:----------|:------|:---------|:--------|:------------|
| count     | Int32 | Yes      | -       | The number of steps, which must be a positive integer.<br>Range: [1, +∞).<br>**Note:**<br>Values less than 1 are treated as 1. |
| end       | Bool  | Yes      | -       | Determines whether the step change occurs at the start or end of each interval.<br>- true: Step change occurs at the end.<br>- false: Step change occurs at the start. |

**Return Value:**

| Type           | Description |
|:---------------|:------------|
| [ICurve](#class-icurve) | Returns the interpolator object of the curve. |

## class ICurve

```cangjie
public class ICurve {}
```

**Function:** A curve object that supports creating different types of curve objects via methods such as [cubicBezierCurve](#static-func-cubicbeziercurvefloat32-float32-float32-float32) and [interpolatingSpring](#static-func-interpolatingspringfloat32-float32-float32-float32) in this module. The curve object can call its member method [interpolate](#func-interpolatefloat32).

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

### func interpolate(Float32)

```cangjie
public func interpolate(fraction: Float32): Float32
```

**Function:** The interpolation calculation function of the interpolation curve, which returns the current interpolation value based on the input normalized time parameter.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type    | Required | Default | Description |
|:----------|:--------|:---------|:--------|:------------|
| fraction  | Float32 | Yes      | -       | The current normalized time parameter.<br>Range