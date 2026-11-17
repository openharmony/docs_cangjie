# ohos.bluetooth.connection（蓝牙connection模块）

<!--Del-->
> **说明：**
>
> 当前为Beta阶段。
<!--DelEnd-->

本模块提供蓝牙设备发现、配对、设备信息查询及设备事件订阅能力。

## 导入模块

```cangjie
import kit.ConnectivityKit.*
```

## 权限列表

ohos.permission.ACCESS_BLUETOOTH

ohos.permission.MANAGE_BLUETOOTH

## 使用说明

示例中的设备地址须替换为实际通过设备发现等接口获取到的地址。示例需按应用场景完成权限声明与授权；设置配对确认还需 MANAGE_BLUETOOTH 权限。

## func getProfileConnectionState(?ProfileId)

```cangjie
public func getProfileConnectionState(profileId!: ?ProfileId = None): ProfileConnectionState
```

**功能：** 获取本机蓝牙 Profile 协议的连接状态。传入 profileId 时返回指定协议的连接状态。不传该参数时，若任一 Profile 已连接，则返回 StateConnected；否则返回 StateDisconnected。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|profileId|?[ProfileId](cj-apis-bluetooth-constant.md#enum-profileid)|否|None|**命名参数。** Profile 协议类型。省略时查询是否存在已连接的 Profile。|

**返回值：**

|类型|说明|
|:---|:---|
|[ProfileConnectionState](cj-apis-bluetooth-constant.md#enum-profileconnectionstate)|指定 Profile 的连接状态；省参时，仅返回 StateConnected 或 StateDisconnected。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900004|Profile not supported.|
|2900099|Operation failed.|

**示例：**

<!-- compile -->

```cangjie
// index.cj

import kit.CangjieKit.BusinessException
import kit.ConnectivityKit.*
import kit.PerformanceAnalysisKit.Hilog

try {
    let state = getProfileConnectionState()
    Hilog.info(0, "Bluetooth", state.toString())
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func pairDevice(String, AsyncCallback\<Unit>)

```cangjie
public func pairDevice(deviceId: String, callback: AsyncCallback<Unit>): Unit
```

**功能：** 向指定远端设备发起配对。通过 callback 返回本次操作的结果；回调成功不表示绑定已完成，绑定状态变化可通过 onBondStateChange 获取。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|deviceId|String|是|-|蓝牙设备地址。示例中的地址需替换为实际获取到的设备地址。|
|callback|[AsyncCallback](../arkinterop/cj-api-business_exception.md#type-asynccallbackt)\<Unit\>|是|-|操作结果回调。成功时 error 为 None、data 为 Some(())；失败时 error 为 BusinessException、data 为 None。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**示例：**

<!-- compile -->

```cangjie
// index.cj

import kit.CangjieKit.BusinessException
import kit.ConnectivityKit.*
import kit.PerformanceAnalysisKit.Hilog

try {
    pairDevice("11:22:33:AA:BB:FF") {
        error: ?BusinessException, result: ?Unit =>
        if (let Some(e) <- error) {
            Hilog.info(0, "Bluetooth", "operation error: ${e.code}")
        } else {
            Hilog.info(0, "Bluetooth", "request completed")
        }
    }
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func getRemoteDeviceName(String)

```cangjie
public func getRemoteDeviceName(deviceId: String): String
```

**功能：** 获取指定远端蓝牙设备的名称或别名。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|deviceId|String|是|-|蓝牙设备地址。示例中的地址需替换为实际获取到的设备地址。|

**返回值：**

|类型|说明|
|:---|:---|
|String|远端蓝牙设备的名称或别名。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Failed to obtain the name or alias of the peer Bluetooth device.|

**示例：**

<!-- compile -->

```cangjie
// index.cj

import kit.CangjieKit.BusinessException
import kit.ConnectivityKit.*
import kit.PerformanceAnalysisKit.Hilog

try {
    let name = getRemoteDeviceName("11:22:33:AA:BB:FF")
    Hilog.info(0, "Bluetooth", name)
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func getRemoteDeviceClass(String)

```cangjie
public func getRemoteDeviceClass(deviceId: String): DeviceClass
```

**功能：** 获取指定远端蓝牙设备的类别信息，包括主要类型、主要和次要组合类型、完整设备类别码。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|deviceId|String|是|-|蓝牙设备地址。示例中的地址需替换为实际获取到的设备地址。|

**返回值：**

|类型|说明|
|:---|:---|
|[DeviceClass](#class-deviceclass)|远端设备的主要类型、组合类型及完整类别码。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**示例：**

<!-- compile -->

```cangjie
// index.cj

import kit.CangjieKit.BusinessException
import kit.ConnectivityKit.*
import kit.PerformanceAnalysisKit.Hilog

try {
    let deviceClass = getRemoteDeviceClass("11:22:33:AA:BB:FF")
    Hilog.info(0, "Bluetooth", deviceClass.majorClass.toString())
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func getLocalName()

```cangjie
public func getLocalName(): String
```

**功能：** 获取本机蓝牙名称。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**返回值：**

|类型|说明|
|:---|:---|
|String|本机蓝牙设备名称。|

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
    let name = getLocalName()
    Hilog.info(0, "Bluetooth", name)
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func getPairedDevices()

```cangjie
public func getPairedDevices(): Array<String>
```

**功能：** 获取与本机已配对的蓝牙设备地址集合。已配对不代表当前已连接。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**返回值：**

|类型|说明|
|:---|:---|
|Array\<String\>|已配对设备地址集合，不表示这些设备当前均已连接。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**示例：**

<!-- compile -->

```cangjie
// index.cj

import kit.CangjieKit.BusinessException
import kit.ConnectivityKit.*
import kit.PerformanceAnalysisKit.Hilog

try {
    let devices = getPairedDevices()
    Hilog.info(0, "Bluetooth", devices.size.toString())
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func getPairState(String)

```cangjie
public func getPairState(deviceId: String): BondState
```

**功能：** 获取指定远端设备的绑定状态。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|deviceId|String|是|-|蓝牙设备地址。示例中的地址需替换为实际获取到的设备地址。|

**返回值：**

|类型|说明|
|:---|:---|
|[BondState](#enum-bondstate)|指定设备的绑定状态。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**示例：**

<!-- compile -->

```cangjie
// index.cj

import kit.CangjieKit.BusinessException
import kit.ConnectivityKit.*
import kit.PerformanceAnalysisKit.Hilog

try {
    let state = getPairState("11:22:33:AA:BB:FF")
    Hilog.info(0, "Bluetooth", state.toString())
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func setDevicePairingConfirmation(String, Bool)

```cangjie
public func setDevicePairingConfirmation(deviceId: String, accept: Bool): Unit
```

**功能：** 确认或拒绝与指定设备的配对请求。accept 为 true 表示接受，false 表示拒绝。应用需具备相应权限。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH 和 ohos.permission.MANAGE_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|deviceId|String|是|-|蓝牙设备地址。示例中的地址需替换为实际获取到的设备地址。|
|accept|Bool|是|-|是否接受配对请求。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**示例：**

<!-- compile -->

```cangjie
// index.cj

import kit.CangjieKit.BusinessException
import kit.ConnectivityKit.*
import kit.PerformanceAnalysisKit.Hilog

try {
    // 仅在存在待处理配对请求且用户已明确同意时调用。
    setDevicePairingConfirmation("11:22:33:AA:BB:FF", true)
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func setDevicePinCode(String, String, AsyncCallback\<Unit>)

```cangjie
public func setDevicePinCode(deviceId: String, code: String, callback: AsyncCallback<Unit>): Unit
```

**功能：** 配对过程中需要用户输入 PIN 码时，提交该 PIN 码。操作结果通过 callback 返回。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|deviceId|String|是|-|蓝牙设备地址。示例中的地址需替换为实际获取到的设备地址。|
|code|String|是|-|用户输入的配对 PIN 码。|
|callback|[AsyncCallback](../arkinterop/cj-api-business_exception.md#type-asynccallbackt)\<Unit\>|是|-|操作结果回调。成功时 error 为 None、data 为 Some(())；失败时 error 为 BusinessException、data 为 None。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**示例：**

<!-- compile -->

```cangjie
// index.cj

import kit.CangjieKit.BusinessException
import kit.ConnectivityKit.*
import kit.PerformanceAnalysisKit.Hilog

try {
    setDevicePinCode("11:22:33:AA:BB:FF", "123456") {
        error: ?BusinessException, result: ?Unit =>
        if (let Some(e) <- error) {
            Hilog.info(0, "Bluetooth", "operation error: ${e.code}")
        } else {
            Hilog.info(0, "Bluetooth", "request completed")
        }
    }
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func setBluetoothScanMode(ScanMode, Int32)

```cangjie
public func setBluetoothScanMode(mode: ScanMode, duration: Int32): Unit
```

**功能：** 设置本机蓝牙扫描模式，即本机是否可被发现或可被连接。duration 表示保持可发现状态的时长，单位为秒。该接口与启动设备发现不同。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|mode|[ScanMode](#enum-scanmode)|是|-|本机的可发现及可连接模式。|
|duration|Int32|是|-|本机保持可发现状态的时长，单位为秒。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**示例：**

<!-- compile -->

```cangjie
// index.cj

import kit.CangjieKit.BusinessException
import kit.ConnectivityKit.*
import kit.PerformanceAnalysisKit.Hilog

try {
    setBluetoothScanMode(ScanMode.ScanModeConnectableGeneralDiscoverable, 120)
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func getBluetoothScanMode()

```cangjie
public func getBluetoothScanMode(): ScanMode
```

**功能：** 获取本机当前的蓝牙扫描模式。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**返回值：**

|类型|说明|
|:---|:---|
|[ScanMode](#enum-scanmode)|本机当前的可发现、可连接模式。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**示例：**

<!-- compile -->

```cangjie
// index.cj

import kit.CangjieKit.BusinessException
import kit.ConnectivityKit.*
import kit.PerformanceAnalysisKit.Hilog

try {
    let mode = getBluetoothScanMode()
    Hilog.info(0, "Bluetooth", mode.toString())
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func startBluetoothDiscovery()

```cangjie
public func startBluetoothDiscovery(): Unit
```

**功能：** 启动蓝牙设备发现。扫描结果通过 onBluetoothDeviceFind 上报；应用应先订阅结果事件，再开始发现。

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
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**示例：**

<!-- compile -->

```cangjie
// index.cj

import kit.CangjieKit.BusinessException
import kit.ConnectivityKit.*
import kit.PerformanceAnalysisKit.Hilog

try {
    startBluetoothDiscovery()
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func stopBluetoothDiscovery()

```cangjie
public func stopBluetoothDiscovery(): Unit
```

**功能：** 停止蓝牙设备发现。

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
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**示例：**

<!-- compile -->

```cangjie
// index.cj

import kit.CangjieKit.BusinessException
import kit.ConnectivityKit.*
import kit.PerformanceAnalysisKit.Hilog

try {
    stopBluetoothDiscovery()
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func isBluetoothDiscovering()

```cangjie
public func isBluetoothDiscovering(): Bool
```

**功能：** 查询本机是否正在进行蓝牙设备发现。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**返回值：**

|类型|说明|
|:---|:---|
|Bool|正在发现设备时返回 true，否则返回 false。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**示例：**

<!-- compile -->

```cangjie
// index.cj

import kit.CangjieKit.BusinessException
import kit.ConnectivityKit.*
import kit.PerformanceAnalysisKit.Hilog

try {
    let discovering = isBluetoothDiscovering()
    Hilog.info(0, "Bluetooth", discovering.toString())
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func onBluetoothDeviceFind(Callback1Argument\<Array\<String>>)

```cangjie
public func onBluetoothDeviceFind(callback: Callback1Argument<Array<String>>): Unit
```

**功能：** 订阅蓝牙设备发现结果，回调携带发现的设备地址集合。该事件仅提供地址信息。地址可能是系统提供的虚拟地址，应使用获取到的地址调用后续设备接口。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|callback|[Callback1Argument](../arkinterop/cj-api-callback_invoke.md#class-callback1argumenta)\<Array\<String\>\>|是|-|事件回调对象，第二个入参携带发现的设备地址集合。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
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

class EventCallback <: Callback1Argument<Array<String>> {
    public func invoke(err: ?BusinessException, arg: Array<String>): Unit {
        if (let Some(e) <- err) {
            Hilog.info(0, "Bluetooth", "event error: ${e.code}")
            return
        }
        Hilog.info(0, "Bluetooth", arg.size.toString())
    }
}

try {
    let listener = EventCallback()
    onBluetoothDeviceFind(listener)
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func offBluetoothDeviceFind(?Callback1Argument\<Array\<String>>)

```cangjie
public func offBluetoothDeviceFind(callback!: ?Callback1Argument<Array<String>> = None): Unit
```

**功能：** 取消订阅蓝牙设备发现结果。传入已注册的同一回调对象可取消指定订阅；不传参数则取消该事件的全部订阅。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|callback|?[Callback1Argument](../arkinterop/cj-api-callback_invoke.md#class-callback1argumenta)\<Array\<String\>\>|否|None|**命名参数。** 取消指定订阅时，应传入注册时使用的同一回调对象；不传或传入 None 时，取消该事件的全部订阅。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
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

class EventCallback <: Callback1Argument<Array<String>> {
    public func invoke(err: ?BusinessException, arg: Array<String>): Unit {
        if (let Some(e) <- err) {
            Hilog.info(0, "Bluetooth", "event error: ${e.code}")
            return
        }
        Hilog.info(0, "Bluetooth", arg.size.toString())
    }
}

try {
    let listener = EventCallback()
    onBluetoothDeviceFind(listener)
    offBluetoothDeviceFind(callback: Some(listener))
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func onBondStateChange(Callback1Argument\<BondStateParam>)

```cangjie
public func onBondStateChange(callback: Callback1Argument<BondStateParam>): Unit
```

**功能：** 订阅远端设备的绑定状态变化事件，回调携带设备地址、绑定状态和解绑原因。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|callback|[Callback1Argument](../arkinterop/cj-api-callback_invoke.md#class-callback1argumenta)\<[BondStateParam](#class-bondstateparam)\>|是|-|事件回调对象，第二个入参携带设备地址、绑定状态及解绑原因。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
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

class EventCallback <: Callback1Argument<BondStateParam> {
    public func invoke(err: ?BusinessException, arg: BondStateParam): Unit {
        if (let Some(e) <- err) {
            Hilog.info(0, "Bluetooth", "event error: ${e.code}")
            return
        }
        Hilog.info(0, "Bluetooth", arg.state.toString())
    }
}

try {
    let listener = EventCallback()
    onBondStateChange(listener)
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func offBondStateChange(?Callback1Argument\<BondStateParam>)

```cangjie
public func offBondStateChange(callback!: ?Callback1Argument<BondStateParam> = None): Unit
```

**功能：** 取消订阅绑定状态变化事件。传入已注册的同一回调对象可取消指定订阅；不传参数则取消该事件的全部订阅。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|callback|?[Callback1Argument](../arkinterop/cj-api-callback_invoke.md#class-callback1argumenta)\<[BondStateParam](#class-bondstateparam)\>|否|None|**命名参数。** 取消指定订阅时，应传入注册时使用的同一回调对象；不传或传入 None 时，取消该事件的全部订阅。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
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

class EventCallback <: Callback1Argument<BondStateParam> {
    public func invoke(err: ?BusinessException, arg: BondStateParam): Unit {
        if (let Some(e) <- err) {
            Hilog.info(0, "Bluetooth", "event error: ${e.code}")
            return
        }
        Hilog.info(0, "Bluetooth", arg.state.toString())
    }
}

try {
    let listener = EventCallback()
    onBondStateChange(listener)
    offBondStateChange(callback: Some(listener))
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func onPinRequired(Callback1Argument\<PinRequiredParam>)

```cangjie
public func onPinRequired(callback: Callback1Argument<PinRequiredParam>): Unit
```

**功能：** 订阅配对过程中的 PIN 请求事件。回调携带设备地址和配对码；应用应结合配对场景处理，不能仅因收到事件就无条件接受配对。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|callback|[Callback1Argument](../arkinterop/cj-api-callback_invoke.md#class-callback1argumenta)\<[PinRequiredParam](#class-pinrequiredparam)\>|是|-|事件回调对象，第二个入参携带设备地址及配对码。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
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

class EventCallback <: Callback1Argument<PinRequiredParam> {
    public func invoke(err: ?BusinessException, arg: PinRequiredParam): Unit {
        if (let Some(e) <- err) {
            Hilog.info(0, "Bluetooth", "event error: ${e.code}")
            return
        }
        Hilog.info(0, "Bluetooth", "Pairing request received")
    }
}

try {
    let listener = EventCallback()
    onPinRequired(listener)
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func offPinRequired(?Callback1Argument\<PinRequiredParam>)

```cangjie
public func offPinRequired(callback!: ?Callback1Argument<PinRequiredParam> = None): Unit
```

**功能：** 取消订阅配对 PIN 请求事件。传入已注册的同一回调对象可取消指定订阅；不传参数则取消该事件的全部订阅。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|callback|?[Callback1Argument](../arkinterop/cj-api-callback_invoke.md#class-callback1argumenta)\<[PinRequiredParam](#class-pinrequiredparam)\>|否|None|**命名参数。** 取消指定订阅时，应传入注册时使用的同一回调对象；不传或传入 None 时，取消该事件的全部订阅。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
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

class EventCallback <: Callback1Argument<PinRequiredParam> {
    public func invoke(err: ?BusinessException, arg: PinRequiredParam): Unit {
        if (let Some(e) <- err) {
            Hilog.info(0, "Bluetooth", "event error: ${e.code}")
            return
        }
        Hilog.info(0, "Bluetooth", "Pairing request received")
    }
}

try {
    let listener = EventCallback()
    onPinRequired(listener)
    offPinRequired(callback: Some(listener))
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func onBatteryChange(Callback1Argument\<BatteryInfo>)

```cangjie
public func onBatteryChange(callback: Callback1Argument<BatteryInfo>): Unit
```

**功能：** 订阅远端设备的电量信息变化事件，回调携带设备电量、左右耳电量及充电盒电量等信息。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|callback|[Callback1Argument](../arkinterop/cj-api-callback_invoke.md#class-callback1argumenta)\<[BatteryInfo](#class-batteryinfo)\>|是|-|事件回调对象，第二个入参携带远端设备电量及充电状态。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
|2900099|Operation failed.|

**示例：**

<!-- compile -->

```cangjie
// index.cj

import ohos.callback_invoke.Callback1Argument
import kit.CangjieKit.BusinessException
import kit.ConnectivityKit.*
import kit.PerformanceAnalysisKit.Hilog

class EventCallback <: Callback1Argument<BatteryInfo> {
    public func invoke(err: ?BusinessException, arg: BatteryInfo): Unit {
        if (let Some(e) <- err) {
            Hilog.info(0, "Bluetooth", "event error: ${e.code}")
            return
        }
        Hilog.info(0, "Bluetooth", arg.batteryLevel.toString())
    }
}

try {
    let listener = EventCallback()
    onBatteryChange(listener)
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func offBatteryChange(?Callback1Argument\<BatteryInfo>)

```cangjie
public func offBatteryChange(callback!: ?Callback1Argument<BatteryInfo> = None): Unit
```

**功能：** 取消订阅远端设备的电量信息变化事件。传入已注册的同一回调对象可取消指定订阅；不传参数则取消该事件的全部订阅。

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|callback|?[Callback1Argument](../arkinterop/cj-api-callback_invoke.md#class-callback1argumenta)\<[BatteryInfo](#class-batteryinfo)\>|否|None|**命名参数。** 取消指定订阅时，应传入注册时使用的同一回调对象；不传或传入 None 时，取消该事件的全部订阅。|

**异常：**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): 对应错误码如下表，详见[通用错误码](../cj-errorcode-universal.md)和[蓝牙服务子系统错误码](cj-errorcode-bluetooth_manager.md)。

|错误码ID|错误信息|
|:---|:---|
|201|Permission denied.|
|2900099|Operation failed.|

**示例：**

<!-- compile -->

```cangjie
// index.cj

import ohos.callback_invoke.Callback1Argument
import kit.CangjieKit.BusinessException
import kit.ConnectivityKit.*
import kit.PerformanceAnalysisKit.Hilog

class EventCallback <: Callback1Argument<BatteryInfo> {
    public func invoke(err: ?BusinessException, arg: BatteryInfo): Unit {
        if (let Some(e) <- err) {
            Hilog.info(0, "Bluetooth", "event error: ${e.code}")
            return
        }
        Hilog.info(0, "Bluetooth", arg.batteryLevel.toString())
    }
}

try {
    let listener = EventCallback()
    onBatteryChange(listener)
    offBatteryChange(callback: Some(listener))
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## class BondStateParam

```cangjie
public class BondStateParam {
    public mut prop deviceId: String
    public mut prop state: BondState
    public mut prop cause: UnbondCause
}
```

**功能：** 绑定状态变化事件参数。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### mut prop deviceId

```cangjie
public mut prop deviceId: String
```

**功能：** 蓝牙设备地址。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**类型：** String

### mut prop state

```cangjie
public mut prop state: BondState
```

**功能：** 设备绑定状态。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**类型：** [BondState](#enum-bondstate)

### mut prop cause

```cangjie
public mut prop cause: UnbondCause
```

**功能：** 解绑原因。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**类型：** [UnbondCause](#enum-unbondcause)

## class PinRequiredParam

```cangjie
public class PinRequiredParam {
    public mut prop deviceId: String
    public mut prop pinCode: String
}
```

**功能：** 设备配对请求参数。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### mut prop deviceId

```cangjie
public mut prop deviceId: String
```

**功能：** 蓝牙设备地址。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**类型：** String

### mut prop pinCode

```cangjie
public mut prop pinCode: String
```

**功能：** 设备配对码。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**类型：** String

## class DeviceClass

```cangjie
public class DeviceClass {
    public mut prop majorClass: MajorClass
    public mut prop majorMinorClass: MajorMinorClass
    public mut prop classOfDevice: Int32
}
```

**功能：** 蓝牙设备的类别信息。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### mut prop majorClass

```cangjie
public mut prop majorClass: MajorClass
```

**功能：** 蓝牙设备的主要类型。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**类型：** [MajorClass](cj-apis-bluetooth-constant.md#enum-majorclass)

### mut prop majorMinorClass

```cangjie
public mut prop majorMinorClass: MajorMinorClass
```

**功能：** 蓝牙设备的主要和次要组合类型。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**类型：** [MajorMinorClass](cj-apis-bluetooth-constant.md#enum-majorminorclass)

### mut prop classOfDevice

```cangjie
public mut prop classOfDevice: Int32
```

**功能：** 完整设备类别码。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**类型：** Int32

## class BatteryInfo

```cangjie
public class BatteryInfo {
    public mut prop batteryLevel: Int32
    public mut prop leftEarBatteryLevel: Int32
    public mut prop leftEarChargeState: DeviceChargeState
    public mut prop rightEarBatteryLevel: Int32
    public mut prop rightEarChargeState: DeviceChargeState
    public mut prop boxBatteryLevel: Int32
    public mut prop boxChargeState: DeviceChargeState
}
```

**功能：** 远端设备的电量信息。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### mut prop batteryLevel

```cangjie
public mut prop batteryLevel: Int32
```

**功能：** 设备电量，-1 表示无电量信息。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**类型：** Int32

### mut prop leftEarBatteryLevel

```cangjie
public mut prop leftEarBatteryLevel: Int32
```

**功能：** 左耳电量，-1 表示无电量信息。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**类型：** Int32

### mut prop leftEarChargeState

```cangjie
public mut prop leftEarChargeState: DeviceChargeState
```

**功能：** 左耳充电状态。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**类型：** [DeviceChargeState](#enum-devicechargestate)

### mut prop rightEarBatteryLevel

```cangjie
public mut prop rightEarBatteryLevel: Int32
```

**功能：** 右耳电量，-1 表示无电量信息。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**类型：** Int32

### mut prop rightEarChargeState

```cangjie
public mut prop rightEarChargeState: DeviceChargeState
```

**功能：** 右耳充电状态。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**类型：** [DeviceChargeState](#enum-devicechargestate)

### mut prop boxBatteryLevel

```cangjie
public mut prop boxBatteryLevel: Int32
```

**功能：** 充电盒电量，-1 表示无电量信息。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**类型：** Int32

### mut prop boxChargeState

```cangjie
public mut prop boxChargeState: DeviceChargeState
```

**功能：** 充电盒充电状态。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**类型：** [DeviceChargeState](#enum-devicechargestate)

## enum ScanMode

```cangjie
public enum ScanMode <: Equatable<ScanMode> & ToString {
    | ScanModeNone
    | ScanModeConnectable
    | ScanModeGeneralDiscoverable
    | ScanModeLimitedDiscoverable
    | ScanModeConnectableGeneralDiscoverable
    | ScanModeConnectableLimitedDiscoverable
    | ...
}
```

**功能：** 本机蓝牙的可发现及可连接模式。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**父类型：**

- Equatable\<ScanMode\>
- ToString

### ScanModeNone

```cangjie
ScanModeNone
```

**功能：** 不可发现且不可连接。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ScanModeConnectable

```cangjie
ScanModeConnectable
```

**功能：** 可连接。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ScanModeGeneralDiscoverable

```cangjie
ScanModeGeneralDiscoverable
```

**功能：** 一般可发现模式。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ScanModeLimitedDiscoverable

```cangjie
ScanModeLimitedDiscoverable
```

**功能：** 受限可发现模式。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ScanModeConnectableGeneralDiscoverable

```cangjie
ScanModeConnectableGeneralDiscoverable
```

**功能：** 可连接且一般可发现。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ScanModeConnectableLimitedDiscoverable

```cangjie
ScanModeConnectableLimitedDiscoverable
```

**功能：** 可连接且受限可发现。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### func !=(ScanMode)

```cangjie
public operator func !=(other: ScanMode): Bool
```

**功能：** 比较两个枚举值是否不相等。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|other|[ScanMode](#enum-scanmode)|是|-|待比较的值。|

**返回值：**

|类型|说明|
|:---|:---|
|Bool|两个枚举值不相同时返回 true，否则返回 false。|

### func ==(ScanMode)

```cangjie
public operator func ==(other: ScanMode): Bool
```

**功能：** 比较两个枚举值是否相等。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|other|[ScanMode](#enum-scanmode)|是|-|待比较的值。|

**返回值：**

|类型|说明|
|:---|:---|
|Bool|两个枚举值相同时返回 true，否则返回 false。|

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

## enum BondState

```cangjie
public enum BondState <: Equatable<BondState> & ToString {
    | BondStateInvalid
    | BondStateBonding
    | BondStateBonded
    | ...
}
```

**功能：** 蓝牙设备的绑定状态。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**父类型：**

- Equatable\<BondState\>
- ToString

### BondStateInvalid

```cangjie
BondStateInvalid
```

**功能：** 未绑定。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### BondStateBonding

```cangjie
BondStateBonding
```

**功能：** 正在绑定。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### BondStateBonded

```cangjie
BondStateBonded
```

**功能：** 已绑定。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### func !=(BondState)

```cangjie
public operator func !=(other: BondState): Bool
```

**功能：** 比较两个枚举值是否不相等。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|other|[BondState](#enum-bondstate)|是|-|待比较的值。|

**返回值：**

|类型|说明|
|:---|:---|
|Bool|两个枚举值不相同时返回 true，否则返回 false。|

### func ==(BondState)

```cangjie
public operator func ==(other: BondState): Bool
```

**功能：** 比较两个枚举值是否相等。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|other|[BondState](#enum-bondstate)|是|-|待比较的值。|

**返回值：**

|类型|说明|
|:---|:---|
|Bool|两个枚举值相同时返回 true，否则返回 false。|

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

## enum DeviceChargeState

```cangjie
public enum DeviceChargeState <: Equatable<DeviceChargeState> & ToString {
    | DeviceNormalChargeNotCharged
    | DeviceNormalChargeInCharging
    | DeviceSuperChargeNotCharged
    | DeviceSuperChargeInCharging
    | ...
}
```

**功能：** 设备是否支持超级快充及当前充电状态。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**父类型：**

- Equatable\<DeviceChargeState\>
- ToString

### DeviceNormalChargeNotCharged

```cangjie
DeviceNormalChargeNotCharged
```

**功能：** 不支持超级快充且未充电。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### DeviceNormalChargeInCharging

```cangjie
DeviceNormalChargeInCharging
```

**功能：** 不支持超级快充且正在充电。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### DeviceSuperChargeNotCharged

```cangjie
DeviceSuperChargeNotCharged
```

**功能：** 支持超级快充且未充电。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### DeviceSuperChargeInCharging

```cangjie
DeviceSuperChargeInCharging
```

**功能：** 支持超级快充且正在充电。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### func !=(DeviceChargeState)

```cangjie
public operator func !=(other: DeviceChargeState): Bool
```

**功能：** 比较两个枚举值是否不相等。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|other|[DeviceChargeState](#enum-devicechargestate)|是|-|待比较的值。|

**返回值：**

|类型|说明|
|:---|:---|
|Bool|两个枚举值不相同时返回 true，否则返回 false。|

### func ==(DeviceChargeState)

```cangjie
public operator func ==(other: DeviceChargeState): Bool
```

**功能：** 比较两个枚举值是否相等。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|other|[DeviceChargeState](#enum-devicechargestate)|是|-|待比较的值。|

**返回值：**

|类型|说明|
|:---|:---|
|Bool|两个枚举值相同时返回 true，否则返回 false。|

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

## enum UnbondCause

```cangjie
public enum UnbondCause <: Equatable<UnbondCause> & ToString {
    | UserRemoved
    | RemoteDeviceDown
    | AuthFailure
    | AuthRejected
    | InternalError
    | ...
}
```

**功能：** 蓝牙设备解绑原因。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**父类型：**

- Equatable\<UnbondCause\>
- ToString

### UserRemoved

```cangjie
UserRemoved
```

**功能：** 用户主动移除设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### RemoteDeviceDown

```cangjie
RemoteDeviceDown
```

**功能：** 远端设备关闭。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### AuthFailure

```cangjie
AuthFailure
```

**功能：** 认证失败，例如 PIN 码错误。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### AuthRejected

```cangjie
AuthRejected
```

**功能：** 远端设备拒绝认证。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### InternalError

```cangjie
InternalError
```

**功能：** 内部错误。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### func !=(UnbondCause)

```cangjie
public operator func !=(other: UnbondCause): Bool
```

**功能：** 比较两个枚举值是否不相等。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|other|[UnbondCause](#enum-unbondcause)|是|-|待比较的值。|

**返回值：**

|类型|说明|
|:---|:---|
|Bool|两个枚举值不相同时返回 true，否则返回 false。|

### func ==(UnbondCause)

```cangjie
public operator func ==(other: UnbondCause): Bool
```

**功能：** 比较两个枚举值是否相等。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|other|[UnbondCause](#enum-unbondcause)|是|-|待比较的值。|

**返回值：**

|类型|说明|
|:---|:---|
|Bool|两个枚举值相同时返回 true，否则返回 false。|

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
