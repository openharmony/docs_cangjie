# ohos.battery_info

This module primarily provides query interfaces for battery status and charging/discharging states.

## Importing the Module

```cangjie
import kit.BasicServicesKit.*
```

## Usage Instructions

API sample code usage instructions:

- If the sample code's first line contains a "// index.cj" comment, it indicates the sample can be compiled and run in the "index.cj" file of the Cangjie template project.
- If the sample requires obtaining the [Context](../AbilityKit/cj-apis-app-ability-ui_ability.md#class-context) application context, it needs to be configured in the "main_ability.cj" file of the Cangjie template project.

For details about the sample project and configuration template mentioned above, refer to [Cangjie Sample Code Instructions](../cj-development-intro.md#Cangjie-Sample-Code-Instructions).

## class BatteryInfo

```cangjie
public class BatteryInfo {}
```

**Function:** Class describing battery information.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### static prop batteryCapacityLevel

```cangjie
public static prop batteryCapacityLevel: BatteryCapacityLevel
```

**Function:** Indicates the current device's battery charge level.

**Type:** [BatteryCapacityLevel](#enum-batterycapacitylevel)

**Read/Write Permission:** Read-only

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### static prop batterySOC

```cangjie
public static prop batterySOC: Int32
```

**Function:** Indicates the current device's remaining battery percentage.

**Type:** Int32

**Read/Write Permission:** Read-only

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### static prop batteryTemperature

```cangjie
public static prop batteryTemperature: Int32
```

**Function:** Indicates the current device's battery temperature.

**Type:** Int32

**Read/Write Permission:** Read-only

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### static prop chargingStatus

```cangjie
public static prop chargingStatus: BatteryChargeState
```

**Function:** Indicates the current device's battery charging status.

**Type:** [BatteryChargeState](#enum-batterychargestate)

**Read/Write Permission:** Read-only

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### static prop healthStatus

```cangjie
public static prop healthStatus: BatteryHealthState
```

**Function:** Indicates the current device's battery health status.

**Type:** [BatteryHealthState](#enum-batteryhealthstate)

**Read/Write Permission:** Read-only

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### static prop isBatteryPresent

```cangjie
public static prop isBatteryPresent: Bool
```

**Function:** Indicates whether the current device supports a battery or if the battery is present.

**Type:** Bool

**Read/Write Permission:** Read-only

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### static prop nowCurrent

```cangjie
public static prop nowCurrent: Int32
```

**Function:** Indicates the current device's battery current.

**Type:** Int32

**Read/Write Permission:** Read-only

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### static prop pluggedType

```cangjie
public static prop pluggedType: BatteryPluggedType
```

**Function:** Indicates the type of charger currently connected to the device.

**Type:** [BatteryPluggedType](#enum-batterypluggedtype)

**Read/Write Permission:** Read-only

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### static prop technology

```cangjie
public static prop technology: String
```

**Function:** Indicates the current device's battery technology model.

**Type:** String

**Read/Write Permission:** Read-only

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### static prop voltage

```cangjie
public static prop voltage: Int32
```

**Function:** Indicates the current device's battery voltage.

**Type:** Int32

**Read/Write Permission:** Read-only

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

## enum BatteryCapacityLevel

```cangjie
public enum BatteryCapacityLevel <: Equatable<BatteryCapacityLevel> & ToString {
    | LevelFull
    | LevelHigh
    | LevelNormal
    | LevelLow
    | LevelWarning
    | LevelCritical
    | LevelShutdown
    | ...
}
```

**Function:** Represents battery charge levels.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

**Parent Types:**

- Equatable\<BatteryCapacityLevel>
- ToString

### LevelCritical

```cangjie
LevelCritical
```

**Function:** Indicates the battery charge level is critically low.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### LevelFull

```cangjie
LevelFull
```

**Function:** Indicates the battery charge level is full.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### LevelHigh

```cangjie
LevelHigh
```

**Function:** Indicates the battery charge level is high.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### LevelLow

```cangjie
LevelLow
```

**Function:** Indicates the battery charge level is low.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### LevelNormal

```cangjie
LevelNormal
```

**Function:** Indicates the battery charge level is normal.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### LevelShutdown

```cangjie
LevelShutdown
```

**Function:** Indicates the battery charge level is at shutdown threshold.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### LevelWarning

```cangjie
LevelWarning
```

**Function:** Indicates the battery charge level is at warning threshold.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### func !=(BatteryCapacityLevel)

```cangjie
public operator func !=(other: BatteryCapacityLevel): Bool
```

**Function:** Performs inequality comparison on battery charge levels.

**Parameters:**

|Parameter|Type|Required|Default|Description|
|:---|:---|:---|:---|:---|
|other|[BatteryCapacityLevel](#enum-batterycapacitylevel)|Yes|-|Battery charge level.|

**Return Value:**

|Type|Description|
|:----|:----|
|Bool| Returns true if battery charge levels differ, otherwise false.|

### func ==(BatteryCapacityLevel)

```cangjie
public operator func ==(other: BatteryCapacityLevel): Bool
```

**Function:** Performs equality comparison on battery charge levels.

**Parameters:**

|Parameter|Type|Required|Default|Description|
|:---|:---|:---|:---|:---|
|other|[BatteryCapacityLevel](#enum-batterycapacitylevel)|Yes|-|Battery charge level.|

**Return Value:**

|Type|Description|
|:----|:----|
|Bool| Returns true if battery charge levels are equal, otherwise false.|

### func toString()

```cangjie
public func toString(): String
```

**Function:** Returns the string representation of the battery charge level.

**Return Value:**

|Type|Description|
|:----|:----|
|String| String corresponding to the battery charge level value. |

## enum BatteryChargeState

```cangjie
public enum BatteryChargeState <: Equatable<BatteryChargeState> & ToString {
    | UnknownChargeState
    | Enabled
    | Disabled
    | Full
    | ...
}
```

**Function:** Represents battery charging states.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

**Parent Types:**

- Equatable\<BatteryChargeState>
- ToString

### Disabled

```cangjie
Disabled
```

**Function:** Indicates the battery charging state is disabled.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### Enabled

```cangjie
Enabled
```

**Function:** Indicates the battery charging state is enabled.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### Full

```cangjie
Full
```

**Function:** Indicates the battery charging state is fully charged.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### UnknownChargeState

```cangjie
UnknownChargeState
```

**Function:** Indicates the battery charging state is unknown.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### func !=(BatteryChargeState)

```cangjie
public operator func !=(other: BatteryChargeState): Bool
```

**Function:** Performs inequality comparison on battery charging states.

**Parameters:**

|Parameter|Type|Required|Default|Description|
|:---|:---|:---|:---|:---|
|other|[BatteryChargeState](#enum-batterychargestate)|Yes|-|Battery charging state.|

**Return Value:**

|Type|Description|
|:----|:----|
|Bool| Returns true if battery charging states differ, otherwise false.|

### func ==(BatteryChargeState)

```cangjie
public operator func ==(other: BatteryChargeState): Bool
```

**Function:** Performs equality comparison on battery charging states.

**Parameters:**

|Parameter|Type|Required|Default|Description|
|:---|:---|:---|:---|:---|
|other|[BatteryChargeState](#enum-batterychargestate)|Yes|-|Battery charging state.|

**Return Value:**

|Type|Description|
|:----|:----|
|Bool| Returns true if battery charging states are equal, otherwise false.|

### func toString()

```cangjie
public func toString(): String
```

**Function:** Returns the string representation of the battery charging state.

**Return Value:**

|Type|Description|
|:----|:----|
|String| String corresponding to the battery charging state value. |## enum BatteryHealthState

```cangjie
public enum BatteryHealthState <: Equatable<BatteryHealthState> & ToString {
    | UnknownHealthState
    | Good
    | Overheat
    | Overvoltage
    | Cold
    | Dead
    | ...
}
```

**Function:** Represents battery health status.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

**Parent Types:**

- Equatable\<BatteryHealthState>
- ToString

### Cold

```cangjie
Cold
```

**Function:** Indicates the battery health status is cold.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### Dead

```cangjie
Dead
```

**Function:** Indicates the battery health status is dead.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### Good

```cangjie
Good
```

**Function:** Indicates the battery health status is normal.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### Overheat

```cangjie
Overheat
```

**Function:** Indicates the battery health status is overheating.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### Overvoltage

```cangjie
Overvoltage
```

**Function:** Indicates the battery health status is overvoltage.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### UnknownHealthState

```cangjie
UnknownHealthState
```

**Function:** Indicates the battery health status is unknown.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### func !=(BatteryHealthState)

```cangjie
public operator func !=(other: BatteryHealthState): Bool
```

**Function:** Compares battery health states for inequality.

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| other | [BatteryHealthState](#enum-batteryhealthstate) | Yes | - | Battery health state. |

**Return Value:**

| Type | Description |
|:----|:----|
| Bool | Returns true if battery health states differ, otherwise false. |

### func ==(BatteryHealthState)

```cangjie
public operator func ==(other: BatteryHealthState): Bool
```

**Function:** Compares battery health states for equality.

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| other | [BatteryHealthState](#enum-batteryhealthstate) | Yes | - | Battery health state. |

**Return Value:**

| Type | Description |
|:----|:----|
| Bool | Returns true if battery health states are identical, otherwise false. |

### func toString()

```cangjie
public func toString(): String
```

**Function:** Returns the string representation of battery health state.

**Return Value:**

| Type | Description |
|:----|:----|
| String | String corresponding to the battery health state value. |

## enum BatteryPluggedType

```cangjie
public enum BatteryPluggedType <: Equatable<BatteryPluggedType> & ToString {
    | UnknownType
    | Ac
    | Usb
    | Wireless
    | ...
}
```

**Function:** Represents the type of connected charger.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

**Parent Types:**

- Equatable\<BatteryPluggedType>
- ToString

### Ac

```cangjie
Ac
```

**Function:** Indicates the connected charger type is AC charger.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### UnknownType

```cangjie
UnknownType
```

**Function:** Indicates the connected charger type is not obtained.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### Usb

```cangjie
Usb
```

**Function:** Indicates the connected charger type is USB.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### Wireless

```cangjie
Wireless
```

**Function:** Indicates the connected charger type is wireless charger.

**System Capability:** SystemCapability.PowerManager.BatteryManager.Core

**Since:** 22

### func !=(BatteryPluggedType)

```cangjie
public operator func !=(other: BatteryPluggedType): Bool
```

**Function:** Compares charger types for inequality.

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| other | [BatteryPluggedType](#enum-batterypluggedtype) | Yes | - | Charger type. |

**Return Value:**

| Type | Description |
|:----|:----|
| Bool | Returns true if charger types differ, otherwise false. |

### func ==(BatteryPluggedType)

```cangjie
public operator func ==(other: BatteryPluggedType): Bool
```

**Function:** Compares charger types for equality.

**Parameters:**

| Parameter | Type | Required | Default | Description |
|:---|:---|:---|:---|:---|
| other | [BatteryPluggedType](#enum-batterypluggedtype) | Yes | - | Charger type. |

**Return Value:**

| Type | Description |
|:----|:----|
| Bool | Returns true if charger types are identical, otherwise false. |

### func toString()

```cangjie
public func toString(): String
```

**Function:** Returns the string representation of charger type information.

**Return Value:**

| Type | Description |
|:----|:----|
| String | String corresponding to the charger type value. |