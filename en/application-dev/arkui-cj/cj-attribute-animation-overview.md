# Overview of Property Animation  

Property interfaces (hereinafter referred to as properties) encompass various types such as dimension properties, layout properties, and position properties, which are used to control component behavior. For components on the current interface, changes to certain properties (e.g., position properties) can trigger UI updates. Adding animations allows property values to transition gradually from a starting point to an endpoint, thereby creating a continuous animation effect. Based on whether animations can be applied during changes, properties can be categorized into animatable properties and non-animatable properties. Two primary criteria determine whether a property is suitable as an animatable property:  

- **Property changes can trigger UI updates.** For example, the [`enabled`](../reference/arkui-cj/cj-universal-attribute-enable.md#func-enabledbool) property controls whether a component can respond to events like clicks or touches, but changes to the `enabled` property do not affect the UI. Thus, it is unsuitable as an animatable property.  

- **The property is suitable for animation transitions during changes.** For instance, the [`focusable`](../reference/arkui-cj/cj-universal-attribute-focus.md#func-focusablebool) property determines whether a component can gain focus. When `focusable` changes, it should immediately switch to the endpoint value to respond to user actions without animation effects, making it unsuitable as an animatable property.  

**Classification of Property Interfaces:**  

- **Animatable Properties:**  

    - **System Animatable Properties:**  

      | Category       | Description                                                                 |
      |:-------------- | :-------------------------------------------------------------------------- |
      | Layout         | Position, size, padding, margin, alignment, weight, etc.                    |
      | Affine Transform | Translation, rotation, scaling, anchor points, etc.                        |
      | Background     | Background color, background blur, etc.                                     |
      | Content        | Font size, text color, image alignment, blur, etc.                          |
      | Foreground     | Foreground color, etc.                                                      |
      | Overlay        | Overlay properties, etc.                                                    |
      | Appearance     | Opacity, rounded corners, borders, shadows, etc.                            |
      | ...            | ...                                                                         |  

    - **Custom Animatable Properties:** Properties abstracted through custom property animation mechanisms.  

- **Non-Animatable Properties:** `zIndex`, `focusable`, etc.  

Typically, the parameter data type of an animatable property must possess continuity—meaning it can be interpolated to fill gaps between data points, achieving a visually smooth effect. However, whether a property's parameter data type supports interpolation is not the sole determinant of its animatability. For example, the [`direction`](../reference/arkui-cj/cj-common-types.md#enum-direction) property, which sets the horizontal layout of an element, has an enumerated parameter data type. Nevertheless, since position properties are animatable, ArkUI also supports adding animations when changes to this property cause component position updates.  

For animatable properties, the system provides not only generic properties but also supports system animatable properties.  

- **System Animatable Properties:** Built-in component properties that support UI updates, such as position, scaling, blur, etc.