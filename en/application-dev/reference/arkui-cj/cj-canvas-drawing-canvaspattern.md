# CanvasPattern

An Object instance created using the createPattern method, which generates an image filling template by specifying an image and repetition method.

## Import Module

```cangjie
import kit.ArkUI.*
```

## class CanvasPattern

```cangjie
public class CanvasPattern {}
```

**Description:** An Object instance created using the createPattern method, which generates an image filling template by specifying an image and repetition method.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

### func setTransform(?Matrix2D)

```cangjie
public func setTransform(transform: ?Matrix2D): Unit
```

**Description:** Applies matrix transformation to the current CanvasPattern using a Matrix2D object as parameter.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 22

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| transform | ?[Matrix2D](./cj-canvas-drawing-matrix2d.md#class-matrix2d) | Yes | - | 2D transformation matrix. |