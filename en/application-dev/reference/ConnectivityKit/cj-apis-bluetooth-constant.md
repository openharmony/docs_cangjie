# ohos.bluetooth.constant (Bluetooth Constant Module)

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

The constant module provides definitions for Bluetooth-related constants.

## Importing the Module

```cangjie
import kit.ConnectivityKit.*
```

## enum ProfileConnectionState

```cangjie
public enum ProfileConnectionState <: Equatable<ProfileConnectionState> & ToString {
    | StateDisconnected
    | StateConnecting
    | StateConnected
    | StateDisconnecting
    | ...
}
```

**Description:** Connection state of a Bluetooth device's profile.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 22

**Parent Types:**

- Equatable\<ProfileConnectionState>
- ToString

### StateConnected

```cangjie
StateConnected
```

**Description:** Indicates the profile is connected.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 22

### StateConnecting

```cangjie
StateConnecting
```

**Description:** Indicates the profile is connecting.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 22

### StateDisconnected

```cangjie
StateDisconnected
```

**Description:** Indicates the profile is disconnected.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 22

### StateDisconnecting

```cangjie
StateDisconnecting
```

**Description:** Indicates the profile is disconnecting.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 22

### func !=(ProfileConnectionState)

```cangjie
public operator func !=(other: ProfileConnectionState): Bool
```

**Description:** Checks inequality of Bluetooth device's profile connection states.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 22

**Parameters:**

| Name | Type | Mandatory | Default Value | Description |
|:---|:---|:---|:---|:---|
| other | [ProfileConnectionState](#enum-profileconnectionstate) | Yes | - | The profile connection state of the Bluetooth device. |

**Return Value:**

| Type | Description |
|:----|:----|
| Bool | Returns true if the profile connection states are different, otherwise returns false. |

### func ==(ProfileConnectionState)

```cangjie
public operator func ==(other: ProfileConnectionState): Bool
```

**Description:** Checks equality of Bluetooth device's profile connection states.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 22

**Parameters:**

| Name | Type | Mandatory | Default Value | Description |
|:---|:---|:---|:---|:---|
| other | [ProfileConnectionState](#enum-profileconnectionstate) | Yes | - | The profile connection state of the Bluetooth device. |

**Return Value:**

| Type | Description |
|:----|:----|
| Bool | Returns true if the profile connection states are identical, otherwise returns false. |

### func toString()

```cangjie
public func toString(): String
```

**Description:** Returns the string representation of the Bluetooth device's profile connection state.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 22

**Return Value:**

| Type | Description |
|:----|:----|
| String | The string representation of the profile connection state. |