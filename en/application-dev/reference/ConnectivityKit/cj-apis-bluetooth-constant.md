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

## enum ProfileId

```cangjie
public enum ProfileId <: Equatable<ProfileId> & ToString {
    | ProfileA2dpSource
    | ProfileHandsfreeAudioGateway
    | ProfileHidHost
    | ProfilePanNetwork
    | ...
}
```

**Description:** Bluetooth profile types.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parent Types:**

- Equatable\<ProfileId\>
- ToString

### ProfileA2dpSource

```cangjie
ProfileA2dpSource
```

**Description:** A2DP Source profile, which is used to send audio data.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ProfileHandsfreeAudioGateway

```cangjie
ProfileHandsfreeAudioGateway
```

**Description:** HFP AG profile, which is used to send call audio data.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ProfileHidHost

```cangjie
ProfileHidHost
```

**Description:** HID Host profile, which is used to establish communication with the HID Device and exchange data.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ProfilePanNetwork

```cangjie
ProfilePanNetwork
```

**Description:** NAP profile, which is used to implement network sharing.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### func !=(ProfileId)

```cangjie
public operator func !=(other: ProfileId): Bool
```

**Description:** Checks whether two enum values are unequal.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|other|[ProfileId](cj-apis-bluetooth-constant.md#enum-profileid)|Yes|-|Value to compare.|

**Return Value:**

|Type|Description|
|:---|:---|
|Bool|Returns true if the two enum values differ; otherwise returns false.|

### func ==(ProfileId)

```cangjie
public operator func ==(other: ProfileId): Bool
```

**Description:** Checks whether two enum values are equal.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|other|[ProfileId](cj-apis-bluetooth-constant.md#enum-profileid)|Yes|-|Value to compare.|

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

## enum MajorClass

```cangjie
public enum MajorClass <: Equatable<MajorClass> & ToString {
    | MajorMisc
    | MajorComputer
    | MajorPhone
    | MajorNetworking
    | MajorAudioVideo
    | MajorPeripheral
    | MajorImaging
    | MajorWearable
    | MajorToy
    | MajorHealth
    | MajorUncategorized
    | ...
}
```

**Description:** Major Bluetooth device classes.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parent Types:**

- Equatable\<MajorClass\>
- ToString

### MajorMisc

```cangjie
MajorMisc
```

**Description:** Miscellaneous device, which that does not belong to any standard category.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### MajorComputer

```cangjie
MajorComputer
```

**Description:** Computer.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### MajorPhone

```cangjie
MajorPhone
```

**Description:** Mobile phone.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### MajorNetworking

```cangjie
MajorNetworking
```

**Description:** LAN or network access point.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### MajorAudioVideo

```cangjie
MajorAudioVideo
```

**Description:** Audio or video device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### MajorPeripheral

```cangjie
MajorPeripheral
```

**Description:** Peripheral device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### MajorImaging

```cangjie
MajorImaging
```

**Description:** Imaging device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### MajorWearable

```cangjie
MajorWearable
```

**Description:** Wearable device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### MajorToy

```cangjie
MajorToy
```

**Description:** Toy.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### MajorHealth

```cangjie
MajorHealth
```

**Description:** Health device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### MajorUncategorized

```cangjie
MajorUncategorized
```

**Description:** Unclassified device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### func !=(MajorClass)

```cangjie
public operator func !=(other: MajorClass): Bool
```

**Description:** Checks whether two enum values are unequal.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|other|[MajorClass](cj-apis-bluetooth-constant.md#enum-majorclass)|Yes|-|Value to compare.|

**Return Value:**

|Type|Description|
|:---|:---|
|Bool|Returns true if the two enum values differ; otherwise returns false.|

### func ==(MajorClass)

```cangjie
public operator func ==(other: MajorClass): Bool
```

**Description:** Checks whether two enum values are equal.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|other|[MajorClass](cj-apis-bluetooth-constant.md#enum-majorclass)|Yes|-|Value to compare.|

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

## enum MajorMinorClass

```cangjie
public enum MajorMinorClass <: Equatable<MajorMinorClass> & ToString {
    | ComputerUncategorized
    | ComputerDesktop
    | ComputerServer
    | ComputerLaptop
    | ComputerHandheldPcPda
    | ComputerPalmSizePcPda
    | ComputerWearable
    | ComputerTablet
    | PhoneUncategorized
    | PhoneCellular
    | PhoneCordless
    | PhoneSmart
    | PhoneModemOrGateway
    | PhoneIsdn
    | NetworkFullyAvailable
    | Network1To17Utilized
    | Network17To33Utilized
    | Network33To50Utilized
    | Network60To67Utilized
    | Network67To83Utilized
    | Network83To99Utilized
    | NetworkNoService
    | AudioVideoUncategorized
    | AudioVideoWearableHeadset
    | AudioVideoHandsfree
    | AudioVideoMicrophone
    | AudioVideoLoudspeaker
    | AudioVideoHeadphones
    | AudioVideoPortableAudio
    | AudioVideoCarAudio
    | AudioVideoSetTopBox
    | AudioVideoHifiAudio
    | AudioVideoVcr
    | AudioVideoVideoCamera
    | AudioVideoCamcorder
    | AudioVideoVideoMonitor
    | AudioVideoVideoDisplayAndLoudspeaker
    | AudioVideoVideoConferencing
    | AudioVideoVideoGamingToy
    | PeripheralNonKeyboardNonPointing
    | PeripheralKeyboard
    | PeripheralPointingDevice
    | PeripheralKeyboardPointing
    | PeripheralUncategorized
    | PeripheralJoystick
    | PeripheralGamepad
    | PeripheralRemoteControl
    | PeripheralSensingDevice
    | PeripheralDigitizerTablet
    | PeripheralCardReader
    | PeripheralDigitalPen
    | PeripheralScannerRfid
    | PeripheralGesturalInput
    | ImagingUncategorized
    | ImagingDisplay
    | ImagingCamera
    | ImagingScanner
    | ImagingPrinter
    | WearableUncategorized
    | WearableWristWatch
    | WearablePager
    | WearableJacket
    | WearableHelmet
    | WearableGlasses
    | ToyUncategorized
    | ToyRobot
    | ToyVehicle
    | ToyDollActionFigure
    | ToyController
    | ToyGame
    | HealthUncategorized
    | HealthBloodPressure
    | HealthThermometer
    | HealthWeighing
    | HealthGlucose
    | HealthPulseOximeter
    | HealthPulseRate
    | HealthDataDisplay
    | HealthStepCounter
    | HealthBodyCompositionAnalyzer
    | HealthPeakFlowMonitor
    | HealthMedicationMonitor
    | HealthKneeProsthesis
    | HealthAnkleProsthesis
    | HealthGenericHealthManager
    | HealthPersonalMobilityDevice
    | ...
}
```

**Description:** Combined major/minor Bluetooth device classes.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parent Types:**

- Equatable\<MajorMinorClass\>
- ToString

### ComputerUncategorized

```cangjie
ComputerUncategorized
```

**Description:** Unclassified computer.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ComputerDesktop

```cangjie
ComputerDesktop
```

**Description:** Desktop computer.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ComputerServer

```cangjie
ComputerServer
```

**Description:** Server.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ComputerLaptop

```cangjie
ComputerLaptop
```

**Description:** Laptop.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ComputerHandheldPcPda

```cangjie
ComputerHandheldPcPda
```

**Description:** Hand-held computer.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ComputerPalmSizePcPda

```cangjie
ComputerPalmSizePcPda
```

**Description:** Palmtop computer.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ComputerWearable

```cangjie
ComputerWearable
```

**Description:** Wearable computer.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ComputerTablet

```cangjie
ComputerTablet
```

**Description:** Tablet.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### PhoneUncategorized

```cangjie
PhoneUncategorized
```

**Description:** Unclassified mobile phone.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### PhoneCellular

```cangjie
PhoneCellular
```

**Description:** Portable phone.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### PhoneCordless

```cangjie
PhoneCordless
```

**Description:** Cordless phone.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### PhoneSmart

```cangjie
PhoneSmart
```

**Description:** Smartphone.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### PhoneModemOrGateway

```cangjie
PhoneModemOrGateway
```

**Description:** Modem or gateway phone.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### PhoneIsdn

```cangjie
PhoneIsdn
```

**Description:** ISDN phone.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### NetworkFullyAvailable

```cangjie
NetworkFullyAvailable
```

**Description:** Network device with a network load of 0%.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### Network1To17Utilized

```cangjie
Network1To17Utilized
```

**Description:** Network device with a network load of 1% to 17%.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### Network17To33Utilized

```cangjie
Network17To33Utilized
```

**Description:** Network device with a network load of 17% to 33%.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### Network33To50Utilized

```cangjie
Network33To50Utilized
```

**Description:** Network device with a network load of 33% to 50%.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### Network60To67Utilized

```cangjie
Network60To67Utilized
```

**Description:** Network device with a network load of 60% to 67%.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### Network67To83Utilized

```cangjie
Network67To83Utilized
```

**Description:** Network device with a network load of 67% to 83%.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### Network83To99Utilized

```cangjie
Network83To99Utilized
```

**Description:** Network device with a network load of 83% to 99%.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### NetworkNoService

```cangjie
NetworkNoService
```

**Description:** Network device with a network load of 100%.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### AudioVideoUncategorized

```cangjie
AudioVideoUncategorized
```

**Description:** Unclassified audio or video device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### AudioVideoWearableHeadset

```cangjie
AudioVideoWearableHeadset
```

**Description:** Wearable audio or video headset.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### AudioVideoHandsfree

```cangjie
AudioVideoHandsfree
```

**Description:** Hands-free audio or video device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### AudioVideoMicrophone

```cangjie
AudioVideoMicrophone
```

**Description:** Audio or video microphone.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### AudioVideoLoudspeaker

```cangjie
AudioVideoLoudspeaker
```

**Description:** Audio or video loudspeaker.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### AudioVideoHeadphones

```cangjie
AudioVideoHeadphones
```

**Description:** Audio or video headphones.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### AudioVideoPortableAudio

```cangjie
AudioVideoPortableAudio
```

**Description:** Portable audio or video device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### AudioVideoCarAudio

```cangjie
AudioVideoCarAudio
```

**Description:** In-vehicle audio or video device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### AudioVideoSetTopBox

```cangjie
AudioVideoSetTopBox
```

**Description:** Audio or video STB device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### AudioVideoHifiAudio

```cangjie
AudioVideoHifiAudio
```

**Description:** High-fidelity audio or video device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### AudioVideoVcr

```cangjie
AudioVideoVcr
```

**Description:** Video cassette recording (VCR) device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### AudioVideoVideoCamera

```cangjie
AudioVideoVideoCamera
```

**Description:** Video camera.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### AudioVideoCamcorder

```cangjie
AudioVideoCamcorder
```

**Description:** Camcorder.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### AudioVideoVideoMonitor

```cangjie
AudioVideoVideoMonitor
```

**Description:** Video monitor.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### AudioVideoVideoDisplayAndLoudspeaker

```cangjie
AudioVideoVideoDisplayAndLoudspeaker
```

**Description:** Video device with a display and speaker.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### AudioVideoVideoConferencing

```cangjie
AudioVideoVideoConferencing
```

**Description:** Video conference device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### AudioVideoVideoGamingToy

```cangjie
AudioVideoVideoGamingToy
```

**Description:** Video gaming toy.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### PeripheralNonKeyboardNonPointing

```cangjie
PeripheralNonKeyboardNonPointing
```

**Description:** Non-keyboard or non-pointing peripheral device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### PeripheralKeyboard

```cangjie
PeripheralKeyboard
```

**Description:** Peripheral keyboard.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### PeripheralPointingDevice

```cangjie
PeripheralPointingDevice
```

**Description:** Pointing peripheral device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### PeripheralKeyboardPointing

```cangjie
PeripheralKeyboardPointing
```

**Description:** Keyboard pointing device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### PeripheralUncategorized

```cangjie
PeripheralUncategorized
```

**Description:** Unclassified peripheral device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### PeripheralJoystick

```cangjie
PeripheralJoystick
```

**Description:** Peripheral joystick.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### PeripheralGamepad

```cangjie
PeripheralGamepad
```

**Description:** Peripheral game pad.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### PeripheralRemoteControl

```cangjie
PeripheralRemoteControl
```

**Description:** Peripheral remote control device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### PeripheralSensingDevice

```cangjie
PeripheralSensingDevice
```

**Description:** Peripheral sensing device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### PeripheralDigitizerTablet

```cangjie
PeripheralDigitizerTablet
```

**Description:** Peripheral digitizer tablet.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### PeripheralCardReader

```cangjie
PeripheralCardReader
```

**Description:** Peripheral card reader.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### PeripheralDigitalPen

```cangjie
PeripheralDigitalPen
```

**Description:** Peripheral digital pen.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### PeripheralScannerRfid

```cangjie
PeripheralScannerRfid
```

**Description:** Peripheral RFID scanner.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### PeripheralGesturalInput

```cangjie
PeripheralGesturalInput
```

**Description:** Gesture input device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ImagingUncategorized

```cangjie
ImagingUncategorized
```

**Description:** Unclassified imaging device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ImagingDisplay

```cangjie
ImagingDisplay
```

**Description:** Imaging display device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ImagingCamera

```cangjie
ImagingCamera
```

**Description:** Imaging camera device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ImagingScanner

```cangjie
ImagingScanner
```

**Description:** Imaging scanner.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ImagingPrinter

```cangjie
ImagingPrinter
```

**Description:** Imaging printer.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### WearableUncategorized

```cangjie
WearableUncategorized
```

**Description:** Unclassified wearable device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### WearableWristWatch

```cangjie
WearableWristWatch
```

**Description:** Smart watch.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### WearablePager

```cangjie
WearablePager
```

**Description:** Wearable pager.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### WearableJacket

```cangjie
WearableJacket
```

**Description:** Wearable jacket.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### WearableHelmet

```cangjie
WearableHelmet
```

**Description:** Wearable helmet.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### WearableGlasses

```cangjie
WearableGlasses
```

**Description:** Wearable glasses.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ToyUncategorized

```cangjie
ToyUncategorized
```

**Description:** Unclassified toy.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ToyRobot

```cangjie
ToyRobot
```

**Description:** Toy robot.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ToyVehicle

```cangjie
ToyVehicle
```

**Description:** Toy vehicle.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ToyDollActionFigure

```cangjie
ToyDollActionFigure
```

**Description:** Humanoid toy doll.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ToyController

```cangjie
ToyController
```

**Description:** Toy controller.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### ToyGame

```cangjie
ToyGame
```

**Description:** Toy gaming device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### HealthUncategorized

```cangjie
HealthUncategorized
```

**Description:** Unclassified health devices.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### HealthBloodPressure

```cangjie
HealthBloodPressure
```

**Description:** Blood pressure device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### HealthThermometer

```cangjie
HealthThermometer
```

**Description:** Thermometer.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### HealthWeighing

```cangjie
HealthWeighing
```

**Description:** Body scale.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### HealthGlucose

```cangjie
HealthGlucose
```

**Description:** Blood glucose monitor.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### HealthPulseOximeter

```cangjie
HealthPulseOximeter
```

**Description:** Pulse oximeter.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### HealthPulseRate

```cangjie
HealthPulseRate
```

**Description:** Heart rate monitor.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### HealthDataDisplay

```cangjie
HealthDataDisplay
```

**Description:** Health data display.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### HealthStepCounter

```cangjie
HealthStepCounter
```

**Description:** Step counter.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### HealthBodyCompositionAnalyzer

```cangjie
HealthBodyCompositionAnalyzer
```

**Description:** Body composition analyzer.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### HealthPeakFlowMonitor

```cangjie
HealthPeakFlowMonitor
```

**Description:** Peak flow monitor.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### HealthMedicationMonitor

```cangjie
HealthMedicationMonitor
```

**Description:** Medication monitor.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### HealthKneeProsthesis

```cangjie
HealthKneeProsthesis
```

**Description:** Prosthetic knee.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### HealthAnkleProsthesis

```cangjie
HealthAnkleProsthesis
```

**Description:** Prosthetic ankle.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### HealthGenericHealthManager

```cangjie
HealthGenericHealthManager
```

**Description:** Generic health management device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### HealthPersonalMobilityDevice

```cangjie
HealthPersonalMobilityDevice
```

**Description:** Personal mobility device.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

### func !=(MajorMinorClass)

```cangjie
public operator func !=(other: MajorMinorClass): Bool
```

**Description:** Checks whether two enum values are unequal.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|other|[MajorMinorClass](cj-apis-bluetooth-constant.md#enum-majorminorclass)|Yes|-|Value to compare.|

**Return Value:**

|Type|Description|
|:---|:---|
|Bool|Returns true if the two enum values differ; otherwise returns false.|

### func ==(MajorMinorClass)

```cangjie
public operator func ==(other: MajorMinorClass): Bool
```

**Description:** Checks whether two enum values are equal.

**System Capability:** SystemCapability.Communication.Bluetooth.Core

**Since:** 26.1.0

**Parameters:**

|Name|Type|Mandatory|Default Value|Description|
|:---|:---|:---|:---|:---|
|other|[MajorMinorClass](cj-apis-bluetooth-constant.md#enum-majorminorclass)|Yes|-|Value to compare.|

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
