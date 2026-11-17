# ohos.bluetooth.connection (Bluetooth Connection Module)

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

Provides Bluetooth device discovery, pairing, device queries, and event subscriptions.

## Importing the Module

```cangjie
import kit.ConnectivityKit.*
```

## Permission List

ohos.permission.ACCESS_BLUETOOTH

ohos.permission.MANAGE_BLUETOOTH

## Usage Instructions

Replace example device addresses with addresses obtained from discovery or device APIs. Declare and obtain the permissions required by each API before running its sample. Pairing confirmation additionally requires MANAGE_BLUETOOTH.

## func getProfileConnectionState(?ProfileId)

```cangjie
public func getProfileConnectionState(profileId!: ?ProfileId = None): ProfileConnectionState
```

**Description:** Obtains the connection state of a Bluetooth profile. When profileId is supplied, returns the state of that profile. When omitted, returns StateConnected if any profile is connected; otherwise returns StateDisconnected.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|profileId|?[ProfileId](cj-apis-bluetooth-constant.md#enum-profileid)|No|None|**Named parameter.** Profile type. Omit this argument to query whether any profile is connected.|

**Return Value:**

|Type|Description|
|:---|:---|
|[ProfileConnectionState](cj-apis-bluetooth-constant.md#enum-profileconnectionstate)|State of the specified profile. Without profileId, returns only StateConnected or StateDisconnected.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900004|Profile not supported.|
|2900099|Operation failed.|

**Example:**

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

**Description:** Starts pairing with the specified remote device. The callback reports the result of this operation, not completion of bonding. Subscribe to onBondStateChange for bonding state changes.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|deviceId|String|Yes|-|Bluetooth device address. Replace the example address with an address obtained from the device APIs.|
|callback|[AsyncCallback](../arkinterop/cj-api-business_exception.md#type-asynccallbackt)\<Unit\>|Yes|-|Operation-result callback. On success, error is None and data is Some(()). On failure, error contains a BusinessException and data is None.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**Example:**

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

**Description:** Obtains the name or alias of the specified remote Bluetooth device.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|deviceId|String|Yes|-|Bluetooth device address. Replace the example address with an address obtained from the device APIs.|

**Return Value:**

|Type|Description|
|:---|:---|
|String|Remote Bluetooth device name or alias.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Failed to obtain the name or alias of the peer Bluetooth device.|

**Example:**

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

**Description:** Obtains the device class, including the major class, combined major/minor class, and complete class-of-device code.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|deviceId|String|Yes|-|Bluetooth device address. Replace the example address with an address obtained from the device APIs.|

**Return Value:**

|Type|Description|
|:---|:---|
|[DeviceClass](#class-deviceclass)|Major class, combined major/minor class, and complete device class code.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**Example:**

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

**Description:** Obtains the local Bluetooth name.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Return Value:**

|Type|Description|
|:---|:---|
|String|Local Bluetooth device name.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900099|Operation failed.|

**Example:**

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

**Description:** Obtains the addresses of devices paired with the local device. A paired device is not necessarily connected.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Return Value:**

|Type|Description|
|:---|:---|
|Array\<String\>|Addresses of paired devices; these devices are not necessarily connected.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**Example:**

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

**Description:** Obtains the bonding state of the specified device.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|deviceId|String|Yes|-|Bluetooth device address. Replace the example address with an address obtained from the device APIs.|

**Return Value:**

|Type|Description|
|:---|:---|
|[BondState](#enum-bondstate)|Bonding state of the specified device.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**Example:**

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

**Description:** Accepts or rejects a pairing request from the specified device. Set accept to true to accept, or false to reject. The caller must have the required permissions.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|deviceId|String|Yes|-|Bluetooth device address. Replace the example address with an address obtained from the device APIs.|
|accept|Bool|Yes|-|Whether to accept the pairing request.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**Example:**

<!-- compile -->

```cangjie
// index.cj

import kit.CangjieKit.BusinessException
import kit.ConnectivityKit.*
import kit.PerformanceAnalysisKit.Hilog

try {
    // Invoke only after the user confirms a pending pairing request.
    setDevicePairingConfirmation("11:22:33:AA:BB:FF", true)
} catch (e: BusinessException) {
    Hilog.info(0, "Bluetooth", "errCode: ${e.code}, errMessage: ${e.message}")
}
```

## func setDevicePinCode(String, String, AsyncCallback\<Unit>)

```cangjie
public func setDevicePinCode(deviceId: String, code: String, callback: AsyncCallback<Unit>): Unit
```

**Description:** Submits the PIN entered by the user when the pairing procedure requests a PIN. The callback reports the operation result.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|deviceId|String|Yes|-|Bluetooth device address. Replace the example address with an address obtained from the device APIs.|
|code|String|Yes|-|Pairing PIN entered by the user.|
|callback|[AsyncCallback](../arkinterop/cj-api-business_exception.md#type-asynccallbackt)\<Unit\>|Yes|-|Operation-result callback. On success, error is None and data is Some(()). On failure, error contains a BusinessException and data is None.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**Example:**

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

**Description:** Sets whether the local device is discoverable or connectable. The duration parameter specifies how long it remains discoverable, in seconds. This operation does not start device discovery.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|mode|[ScanMode](#enum-scanmode)|Yes|-|Local discoverability and connectability mode.|
|duration|Int32|Yes|-|Discoverable duration, in seconds.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**Example:**

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

**Description:** Obtains the current local Bluetooth scan mode.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Return Value:**

|Type|Description|
|:---|:---|
|[ScanMode](#enum-scanmode)|Current local discoverability and connectability mode.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**Example:**

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

**Description:** Starts Bluetooth device discovery. Register onBluetoothDeviceFind before starting discovery to receive device addresses.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**Example:**

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

**Description:** Stops Bluetooth device discovery.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**Example:**

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

**Description:** Checks whether Bluetooth device discovery is running.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Return Value:**

|Type|Description|
|:---|:---|
|Bool|Returns true while discovering devices; otherwise false.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900001|Service stopped.|
|2900003|Bluetooth disabled.|
|2900099|Operation failed.|

**Example:**

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

**Description:** Subscribes to device-discovery results containing device addresses only. Addresses may be virtual addresses supplied by the system; use the returned addresses for subsequent device operations.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|callback|[Callback1Argument](../arkinterop/cj-api-callback_invoke.md#class-callback1argumenta)\<Array\<String\>\>|Yes|-|Event callback object. Its second argument contains discovered device addresses.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900099|Operation failed.|

**Example:**

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

**Description:** Unsubscribes from device-discovery results. Supply the same registered callback object to remove one subscription, or omit it to remove all subscriptions for this event.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|callback|?[Callback1Argument](../arkinterop/cj-api-callback_invoke.md#class-callback1argumenta)\<Array\<String\>\>|No|None|**Named parameter.** Pass the same registered callback object to remove that subscription. Omit it or pass None to remove all subscriptions for this event.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900099|Operation failed.|

**Example:**

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

**Description:** Subscribes to bonding-state changes. The callback receives the device address, bonding state, and unbonding cause.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|callback|[Callback1Argument](../arkinterop/cj-api-callback_invoke.md#class-callback1argumenta)\<[BondStateParam](#class-bondstateparam)\>|Yes|-|Event callback object. Its second argument contains device address, bonding state, and unbonding cause.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900099|Operation failed.|

**Example:**

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

**Description:** Unsubscribes from bonding-state changes. Supply the same registered callback object, or omit it to remove all subscriptions for this event.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|callback|?[Callback1Argument](../arkinterop/cj-api-callback_invoke.md#class-callback1argumenta)\<[BondStateParam](#class-bondstateparam)\>|No|None|**Named parameter.** Pass the same registered callback object to remove that subscription. Omit it or pass None to remove all subscriptions for this event.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900099|Operation failed.|

**Example:**

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

**Description:** Subscribes to pairing PIN requests, including the device address and pairing code. Handle the request according to the pairing scenario; do not automatically accept every request.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|callback|[Callback1Argument](../arkinterop/cj-api-callback_invoke.md#class-callback1argumenta)\<[PinRequiredParam](#class-pinrequiredparam)\>|Yes|-|Event callback object. Its second argument contains device address and pairing code.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900099|Operation failed.|

**Example:**

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

**Description:** Unsubscribes from pairing PIN requests. Supply the same registered callback object, or omit it to remove all subscriptions for this event.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|callback|?[Callback1Argument](../arkinterop/cj-api-callback_invoke.md#class-callback1argumenta)\<[PinRequiredParam](#class-pinrequiredparam)\>|No|None|**Named parameter.** Pass the same registered callback object to remove that subscription. Omit it or pass None to remove all subscriptions for this event.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|801|Capability not supported.|
|2900099|Operation failed.|

**Example:**

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

**Description:** Subscribes to remote-device battery changes, including the device, left/right earbuds, and charging case.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|callback|[Callback1Argument](../arkinterop/cj-api-callback_invoke.md#class-callback1argumenta)\<[BatteryInfo](#class-batteryinfo)\>|Yes|-|Event callback object. Its second argument contains remote-device battery and charging state.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|2900099|Operation failed.|

**Example:**

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

**Description:** Unsubscribes from remote-device battery changes. Supply the same registered callback object, or omit it to remove all subscriptions for this event.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|callback|?[Callback1Argument](../arkinterop/cj-api-callback_invoke.md#class-callback1argumenta)\<[BatteryInfo](#class-batteryinfo)\>|No|None|**Named parameter.** Pass the same registered callback object to remove that subscription. Omit it or pass None to remove all subscriptions for this event.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
|201|Permission denied.|
|2900099|Operation failed.|

**Example:**

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

**Description:** Bonding-state-change event parameters.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### mut prop deviceId

```cangjie
public mut prop deviceId: String
```

**Description:** Bluetooth device address.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Type:** String

### mut prop state

```cangjie
public mut prop state: BondState
```

**Description:** Device bonding state.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Type:** [BondState](#enum-bondstate)

### mut prop cause

```cangjie
public mut prop cause: UnbondCause
```

**Description:** Cause of unbonding.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Type:** [UnbondCause](#enum-unbondcause)

## class PinRequiredParam

```cangjie
public class PinRequiredParam {
    public mut prop deviceId: String
    public mut prop pinCode: String
}
```

**Description:** Pairing-request parameters.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### mut prop deviceId

```cangjie
public mut prop deviceId: String
```

**Description:** Bluetooth device address.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Type:** String

### mut prop pinCode

```cangjie
public mut prop pinCode: String
```

**Description:** Pairing code.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Type:** String

## class DeviceClass

```cangjie
public class DeviceClass {
    public mut prop majorClass: MajorClass
    public mut prop majorMinorClass: MajorMinorClass
    public mut prop classOfDevice: Int32
}
```

**Description:** Bluetooth device class information.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### mut prop majorClass

```cangjie
public mut prop majorClass: MajorClass
```

**Description:** Major device class.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Type:** [MajorClass](cj-apis-bluetooth-constant.md#enum-majorclass)

### mut prop majorMinorClass

```cangjie
public mut prop majorMinorClass: MajorMinorClass
```

**Description:** Combined major/minor device class.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Type:** [MajorMinorClass](cj-apis-bluetooth-constant.md#enum-majorminorclass)

### mut prop classOfDevice

```cangjie
public mut prop classOfDevice: Int32
```

**Description:** Complete class-of-device code.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Type:** Int32

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

**Description:** Remote-device battery information.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### mut prop batteryLevel

```cangjie
public mut prop batteryLevel: Int32
```

**Description:** Device battery level; -1 means no battery information.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Type:** Int32

### mut prop leftEarBatteryLevel

```cangjie
public mut prop leftEarBatteryLevel: Int32
```

**Description:** Left-earbud battery level; -1 means no information.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Type:** Int32

### mut prop leftEarChargeState

```cangjie
public mut prop leftEarChargeState: DeviceChargeState
```

**Description:** Left-earbud charging state.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Type:** [DeviceChargeState](#enum-devicechargestate)

### mut prop rightEarBatteryLevel

```cangjie
public mut prop rightEarBatteryLevel: Int32
```

**Description:** Right-earbud battery level; -1 means no information.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Type:** Int32

### mut prop rightEarChargeState

```cangjie
public mut prop rightEarChargeState: DeviceChargeState
```

**Description:** Right-earbud charging state.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Type:** [DeviceChargeState](#enum-devicechargestate)

### mut prop boxBatteryLevel

```cangjie
public mut prop boxBatteryLevel: Int32
```

**Description:** Charging-case battery level; -1 means no information.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Type:** Int32

### mut prop boxChargeState

```cangjie
public mut prop boxChargeState: DeviceChargeState
```

**Description:** Charging-case charging state.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Type:** [DeviceChargeState](#enum-devicechargestate)

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

**Description:** Local Bluetooth discoverability and connectability modes.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parent Types:**

- Equatable\<ScanMode\>
- ToString

### ScanModeNone

```cangjie
ScanModeNone
```

**Description:** Indicates the scan mode is none.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ScanModeConnectable

```cangjie
ScanModeConnectable
```

**Description:** Indicates the scan mode is connectable.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ScanModeGeneralDiscoverable

```cangjie
ScanModeGeneralDiscoverable
```

**Description:** Indicates the scan mode is general discoverable.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ScanModeLimitedDiscoverable

```cangjie
ScanModeLimitedDiscoverable
```

**Description:** Indicates the scan mode is limited discoverable.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ScanModeConnectableGeneralDiscoverable

```cangjie
ScanModeConnectableGeneralDiscoverable
```

**Description:** Indicates the scan mode is connectable and general discoverable.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ScanModeConnectableLimitedDiscoverable

```cangjie
ScanModeConnectableLimitedDiscoverable
```

**Description:** Indicates the scan mode is connectable and limited discoverable.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### func !=(ScanMode)

```cangjie
public operator func !=(other: ScanMode): Bool
```

**Description:** Checks whether two enum values are unequal.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|other|[ScanMode](#enum-scanmode)|Yes|-|Value to compare.|

**Return Value:**

|Type|Description|
|:---|:---|
|Bool|Returns true if the two enum values differ; otherwise returns false.|

### func ==(ScanMode)

```cangjie
public operator func ==(other: ScanMode): Bool
```

**Description:** Checks whether two enum values are equal.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|other|[ScanMode](#enum-scanmode)|Yes|-|Value to compare.|

**Return Value:**

|Type|Description|
|:---|:---|
|Bool|Returns true if the two enum values are equal; otherwise returns false.|

### func toString()

```cangjie
public func toString(): String
```

**Description:** Returns the string representation of the enum value.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Return Value:**

|Type|Description|
|:---|:---|
|String|String representation of the enum value.|

## enum BondState

```cangjie
public enum BondState <: Equatable<BondState> & ToString {
    | BondStateInvalid
    | BondStateBonding
    | BondStateBonded
    | ...
}
```

**Description:** Bluetooth device bonding states.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parent Types:**

- Equatable\<BondState\>
- ToString

### BondStateInvalid

```cangjie
BondStateInvalid
```

**Description:** Indicate the bond state is invalid.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### BondStateBonding

```cangjie
BondStateBonding
```

**Description:** Indicate the bond state is bonding.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### BondStateBonded

```cangjie
BondStateBonded
```

**Description:** Indicate the bond state is bonded.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### func !=(BondState)

```cangjie
public operator func !=(other: BondState): Bool
```

**Description:** Checks whether two enum values are unequal.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|other|[BondState](#enum-bondstate)|Yes|-|Value to compare.|

**Return Value:**

|Type|Description|
|:---|:---|
|Bool|Returns true if the two enum values differ; otherwise returns false.|

### func ==(BondState)

```cangjie
public operator func ==(other: BondState): Bool
```

**Description:** Checks whether two enum values are equal.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|other|[BondState](#enum-bondstate)|Yes|-|Value to compare.|

**Return Value:**

|Type|Description|
|:---|:---|
|Bool|Returns true if the two enum values are equal; otherwise returns false.|

### func toString()

```cangjie
public func toString(): String
```

**Description:** Returns the string representation of the enum value.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Return Value:**

|Type|Description|
|:---|:---|
|String|String representation of the enum value.|

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

**Description:** Charging status and whether the device supports super charging.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parent Types:**

- Equatable\<DeviceChargeState\>
- ToString

### DeviceNormalChargeNotCharged

```cangjie
DeviceNormalChargeNotCharged
```

**Description:** Not support super charge, and not charged.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### DeviceNormalChargeInCharging

```cangjie
DeviceNormalChargeInCharging
```

**Description:** Not support super charge, and in charging.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### DeviceSuperChargeNotCharged

```cangjie
DeviceSuperChargeNotCharged
```

**Description:** Support super charge, and not charged.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### DeviceSuperChargeInCharging

```cangjie
DeviceSuperChargeInCharging
```

**Description:** Support super charge, and in charging.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### func !=(DeviceChargeState)

```cangjie
public operator func !=(other: DeviceChargeState): Bool
```

**Description:** Checks whether two enum values are unequal.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|other|[DeviceChargeState](#enum-devicechargestate)|Yes|-|Value to compare.|

**Return Value:**

|Type|Description|
|:---|:---|
|Bool|Returns true if the two enum values differ; otherwise returns false.|

### func ==(DeviceChargeState)

```cangjie
public operator func ==(other: DeviceChargeState): Bool
```

**Description:** Checks whether two enum values are equal.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|other|[DeviceChargeState](#enum-devicechargestate)|Yes|-|Value to compare.|

**Return Value:**

|Type|Description|
|:---|:---|
|Bool|Returns true if the two enum values are equal; otherwise returns false.|

### func toString()

```cangjie
public func toString(): String
```

**Description:** Returns the string representation of the enum value.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Return Value:**

|Type|Description|
|:---|:---|
|String|String representation of the enum value.|

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

**Description:** Causes of Bluetooth device unbonding.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parent Types:**

- Equatable\<UnbondCause\>
- ToString

### UserRemoved

```cangjie
UserRemoved
```

**Description:** User proactively removed device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### RemoteDeviceDown

```cangjie
RemoteDeviceDown
```

**Description:** Remote device shut down.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### AuthFailure

```cangjie
AuthFailure
```

**Description:** Wrong PIN code.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### AuthRejected

```cangjie
AuthRejected
```

**Description:** Remote device rejected.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### InternalError

```cangjie
InternalError
```

**Description:** Internal error.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### func !=(UnbondCause)

```cangjie
public operator func !=(other: UnbondCause): Bool
```

**Description:** Checks whether two enum values are unequal.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|other|[UnbondCause](#enum-unbondcause)|Yes|-|Value to compare.|

**Return Value:**

|Type|Description|
|:---|:---|
|Bool|Returns true if the two enum values differ; otherwise returns false.|

### func ==(UnbondCause)

```cangjie
public operator func ==(other: UnbondCause): Bool
```

**Description:** Checks whether two enum values are equal.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|other|[UnbondCause](#enum-unbondcause)|Yes|-|Value to compare.|

**Return Value:**

|Type|Description|
|:---|:---|
|Bool|Returns true if the two enum values are equal; otherwise returns false.|

### func toString()

```cangjie
public func toString(): String
```

**Description:** Returns the string representation of the enum value.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Return Value:**

|Type|Description|
|:---|:---|
|String|String representation of the enum value.|
