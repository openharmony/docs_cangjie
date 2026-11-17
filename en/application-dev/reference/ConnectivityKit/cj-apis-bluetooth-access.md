# ohos.bluetooth.access (Bluetooth Access Module)

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

Provides Bluetooth switch control, state queries, and state-change subscriptions.

## Importing the Module

```cangjie
import kit.ConnectivityKit.*
```

## Permission List

ohos.permission.ACCESS_BLUETOOTH

## Usage Instructions

Declare and obtain the required permissions before running the samples.

## func enableBluetooth()

```cangjie
public func enableBluetooth(): Unit
```

**Description:** Enables Bluetooth. Subscribe to onStateChange to observe Bluetooth state changes. Query getState first to avoid repeatedly enabling Bluetooth.

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
|2900099|Operation failed.|

**Example:**

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

**Description:** Disables Bluetooth. Subscribe to onStateChange to observe Bluetooth state changes.

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
|2900099|Operation failed.|

**Example:**

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

**Description:** Obtains the local Bluetooth state.

**Required Permissions:** ohos.permission.ACCESS_BLUETOOTH

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Return Value:**

|Type|Description|
|:---|:---|
|[BluetoothState](#enum-bluetoothstate)|Local Bluetooth state.|

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

**Description:** Subscribes to local Bluetooth state changes. The callback receives the new BluetoothState.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|callback|[Callback1Argument](../arkinterop/cj-api-callback_invoke.md#class-callback1argumenta)\<[BluetoothState](#enum-bluetoothstate)\>|Yes|-|Event callback object. Its second argument contains updated Bluetooth state.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
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

**Description:** Unsubscribes from local Bluetooth state changes. Pass the same registered callback object to remove that subscription, or omit the argument to remove all state-change subscriptions.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|callback|?[Callback1Argument](../arkinterop/cj-api-callback_invoke.md#class-callback1argumenta)\<[BluetoothState](#enum-bluetoothstate)\>|No|None|**Named parameter.** Pass the same registered callback object to remove that subscription. Omit it or pass None to remove all subscriptions for this event.|

**Exceptions:**

- [BusinessException](../arkinterop/cj-api-business_exception.md#class-businessexception): For details, see [Universal Error Codes](../cj-errorcode-universal.md) and [Bluetooth Error Codes](cj-errorcode-bluetooth_manager.md).

|Code|Message|
|:---|:---|
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
    offStateChange(callback: Some(listener))
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

**Description:** Bluetooth states, including normal mode and BLE-only mode.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parent Types:**

- Equatable\<BluetoothState\>
- ToString

### StateOff

```cangjie
StateOff
```

**Description:** Indicates the local Bluetooth is off.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### StateTurningOn

```cangjie
StateTurningOn
```

**Description:** Indicates the local Bluetooth is turning on.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### StateOn

```cangjie
StateOn
```

**Description:** Indicates the local Bluetooth is on, and ready for use.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### StateTurningOff

```cangjie
StateTurningOff
```

**Description:** Indicates the local Bluetooth is turning off.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### StateBleTurningOn

```cangjie
StateBleTurningOn
```

**Description:** Indicates the local Bluetooth is turning LE mode on.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### StateBleOn

```cangjie
StateBleOn
```

**Description:** Indicates that the local device is in BLE-only mode.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### StateBleTurningOff

```cangjie
StateBleTurningOff
```

**Description:** Indicates the local Bluetooth is turning off LE only mode.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### func !=(BluetoothState)

```cangjie
public operator func !=(other: BluetoothState): Bool
```

**Description:** Checks whether two enum values are unequal.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|other|[BluetoothState](#enum-bluetoothstate)|Yes|-|Value to compare.|

**Return Value:**

|Type|Description|
|:---|:---|
|Bool|Returns true if the two enum values differ; otherwise returns false.|

### func ==(BluetoothState)

```cangjie
public operator func ==(other: BluetoothState): Bool
```

**Description:** Checks whether two enum values are equal.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|other|[BluetoothState](#enum-bluetoothstate)|Yes|-|Value to compare.|

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
