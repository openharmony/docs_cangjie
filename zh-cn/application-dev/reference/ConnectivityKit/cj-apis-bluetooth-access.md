# ohos.bluetooth.access（蓝牙access模块）

<!--Del-->
> **说明：**
>
> 当前为Beta阶段。
<!--DelEnd-->

本模块提供蓝牙开关控制、状态查询和状态变化订阅能力。

## 导入模块

```cangjie
import kit.ConnectivityKit.*
```

## 权限列表

ohos.permission.ACCESS_BLUETOOTH

## 使用说明

示例需要按应用场景完成权限声明与授权。示例中的 `// index.cj` 表示代码放置位置，具体工程配置请参见[仓颉示例代码说明](../cj-development-intro.md#仓颉示例代码说明)。

开启或关闭蓝牙的调用返回，不代表蓝牙状态切换已经完成。需要观察实际状态时，请使用 [getState](#func-getstate) 或订阅 [onStateChange](#func-onstatechangecallback1argumentbluetoothstate)。

## func enableBluetooth()

```cangjie
public func enableBluetooth(): Unit
```

**功能：** 开启蓝牙。建议先通过 [getState](#func-getstate) 查询当前状态，在 [StateOff](#stateoff) 状态下调用；通过 [onStateChange](#func-onstatechangecallback1argumentbluetoothstate) 观察状态变化。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900099|Operation failed.|

**示例：**

<!-- compile -->

```cangjie
// index.cj

import kit.CangjieKit.BusinessException
import kit.ConnectivityKit.*
import kit.PerformanceAnalysisKit.Hilog

try {
    enableBluetooth()
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func disableBluetooth()

```cangjie
public func disableBluetooth(): Unit
```

**功能：** 关闭蓝牙。通过 [onStateChange](#func-onstatechangecallback1argumentbluetoothstate) 观察状态变化。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900099|Operation failed.|

**示例：**

<!-- compile -->

```cangjie
// index.cj

import kit.CangjieKit.BusinessException
import kit.ConnectivityKit.*
import kit.PerformanceAnalysisKit.Hilog

try {
    disableBluetooth()
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func getState()

```cangjie
public func getState(): BluetoothState
```

**功能：** 获取本端蓝牙开关状态。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**返回值：**

|类型|说明|
|:---|:---|
|[BluetoothState](#enum-bluetoothstate)|本端蓝牙开关状态。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900099|Operation failed.|

**示例：**

<!-- compile -->

```cangjie
// index.cj

import kit.CangjieKit.BusinessException
import kit.ConnectivityKit.*
import kit.PerformanceAnalysisKit.Hilog

try {
    let state = getState()
    Hilog.info(0, "Bluetooth", state.toString())
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func onStateChange(Callback1Argument\<BluetoothState>)

```cangjie
public func onStateChange(callback: Callback1Argument<BluetoothState>): Unit
```

**功能：** 订阅本端蓝牙开关状态变化事件，回调携带新的 BluetoothState。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|callback|[Callback1Argument](../arkinterop/cj-api-callback_invoke.md#class-callback1argumenta)\<[BluetoothState](#enum-bluetoothstate)\>|是|-|事件回调对象，第二个入参携带变化后的蓝牙开关状态。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|801|Capability not supported.|
|2900099|Operation failed.|

**示例：**

<!-- compile -->

```cangjie
// index.cj

import ohos.callback_invoke.Callback1Argument
import kit.CangjieKit.BusinessException
import kit.ConnectivityKit.*
import kit.PerformanceAnalysisKit.Hilog

class EventCallback <: Callback1Argument<BluetoothState> {
    public func invoke(err: ?BusinessException, arg: BluetoothState): Unit {
        if (let Some(e) <- err) {
            Hilog.info(0, "Bluetooth", "event error: ${e.code}")
            return
        }
        Hilog.info(0, "Bluetooth", arg.toString())
    }
}

try {
    let listener = EventCallback()
    onStateChange(listener)
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func offStateChange(?Callback1Argument\<BluetoothState>)

```cangjie
public func offStateChange(callback!: ?Callback1Argument<BluetoothState> = None): Unit
```

**功能：** 取消订阅本端蓝牙开关状态变化事件。传入已注册的同一回调对象可取消指定订阅；不传参数时取消全部状态变化订阅。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|callback|?[Callback1Argument](../arkinterop/cj-api-callback_invoke.md#class-callback1argumenta)\<[BluetoothState](#enum-bluetoothstate)\>|否|None|**命名参数。** 取消指定订阅时，应传入注册时使用的同一回调对象；不传或传入 None 时，取消该事件的全部订阅。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|801|Capability not supported.|
|2900099|Operation failed.|

**示例：**

<!-- compile -->

```cangjie
// index.cj

import ohos.callback_invoke.Callback1Argument
import kit.CangjieKit.BusinessException
import kit.ConnectivityKit.*
import kit.PerformanceAnalysisKit.Hilog

class EventCallback <: Callback1Argument<BluetoothState> {
    public func invoke(err: ?BusinessException, arg: BluetoothState): Unit {
        if (let Some(e) <- err) {
            Hilog.info(0, "Bluetooth", "event error: ${e.code}")
            return
        }
        Hilog.info(0, "Bluetooth", arg.toString())
    }
}

try {
    let listener = EventCallback()
    onStateChange(listener)
    // 在不再需要接收事件时，传入注册时使用的同一对象。
    offStateChange(callback: Some(listener))
    // 不传参数可取消全部状态变化订阅。
    offStateChange()
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## enum BluetoothState

```cangjie
public enum BluetoothState <: Equatable<BluetoothState> & ToString {
    | StateOff
    | StateTurningOn
    | StateOn
    | StateTurningOff
    | StateBleTurningOn
    | StateBleOn
    | StateBleTurningOff
    | ...
}
```

**功能：** 蓝牙开关状态枚举，包含普通蓝牙模式及仅低功耗蓝牙（BLE）模式的状态。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**父类型：**

- Equatable\<BluetoothState\>
- ToString

### StateOff

```cangjie
StateOff
```

**功能：** 蓝牙已关闭。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### StateTurningOn

```cangjie
StateTurningOn
```

**功能：** 蓝牙正在开启。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### StateOn

```cangjie
StateOn
```

**功能：** 表示本端蓝牙已开启，可以使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### StateTurningOff

```cangjie
StateTurningOff
```

**功能：** 蓝牙正在关闭。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### StateBleTurningOn

```cangjie
StateBleTurningOn
```

**功能：** 正在开启 BLE 模式。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### StateBleOn

```cangjie
StateBleOn
```

**功能：** 表示本端处于仅低功耗蓝牙（BLE）模式。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### StateBleTurningOff

```cangjie
StateBleTurningOff
```

**功能：** 表示本端正在关闭仅低功耗蓝牙（BLE）模式。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### func !=(BluetoothState)

```cangjie
public operator func !=(other: BluetoothState): Bool
```

**功能：** 比较两个枚举值是否不相等。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|other|[BluetoothState](#enum-bluetoothstate)|是|-|待比较的值。|

**返回值：**

|类型|说明|
|:---|:---|
|Bool|两个蓝牙状态不相同时返回 true，否则返回 false。|

### func ==(BluetoothState)

```cangjie
public operator func ==(other: BluetoothState): Bool
```

**功能：** 比较两个枚举值是否相等。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|other|[BluetoothState](#enum-bluetoothstate)|是|-|待比较的值。|

**返回值：**

|类型|说明|
|:---|:---|
|Bool|两个蓝牙状态相同时返回 true，否则返回 false。|

### func toString()

```cangjie
public func toString(): String
```

**功能：** 返回枚举值的字符串表示。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**返回值：**

|类型|说明|
|:---|:---|
|String|枚举值的字符串表示。|
