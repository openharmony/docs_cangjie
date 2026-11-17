# ohos.bluetooth.constant（蓝牙constant模块）

<!--Del-->
> **说明：**
>
> 当前为Beta阶段。
<!--DelEnd-->

constant模块提供了蓝牙中常量的定义。

## 导入模块

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

**功能：** 蓝牙设备的 profile 连接状态。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 22

**父类型：**

- Equatable\<[ProfileConnectionState](#enum-profileconnectionstate)>
- ToString

### StateConnected

```cangjie
StateConnected
```

**功能：** 表示profile已连接。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 22

### StateConnecting

```cangjie
StateConnecting
```

**功能：** 表示profile正在连接。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 22

### StateDisconnected

```cangjie
StateDisconnected
```

**功能：** 表示profile已断连。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 22

### StateDisconnecting

```cangjie
StateDisconnecting
```

**功能：** 表示profile正在断开连接。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 22

### func !=(ProfileConnectionState)

```cangjie
public operator func !=(other: ProfileConnectionState): Bool
```

**功能：** 对蓝牙设备的 profile 连接状态判不等。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 22

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|other|[ProfileConnectionState](#enum-profileconnectionstate)|是|-|蓝牙设备的 profile 连接状态。|

**返回值：**

|类型|说明|
|:----|:----|
|Bool|如果蓝牙设备的 profile 连接状态不同返回 true，否则返回 false。|

### func ==(ProfileConnectionState)

```cangjie
public operator func ==(other: ProfileConnectionState): Bool
```

**功能：** 对蓝牙设备的 profile 连接状态进行判等。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 22

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|other|[ProfileConnectionState](#enum-profileconnectionstate)|是|-|蓝牙设备的 profile 连接状态。|

**返回值：**

|类型|说明|
|:----|:----|
|Bool|如果蓝牙设备的 profile 连接状态相同返回 true，否则返回 false。|

### func toString()

```cangjie
public func toString(): String
```

**功能：** 返回蓝牙设备的 profile 连接状态的字符串表示。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 22

**返回值：**

|类型|说明|
|:----|:----|
|String|蓝牙设备的 profile 连接状态的字符串表示。|

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

**功能：** 蓝牙 Profile 协议类型。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**父类型：**

- Equatable\<ProfileId\>
- ToString

### ProfileA2dpSource

```cangjie
ProfileA2dpSource
```

**功能：** A2DP Source Profile，负责发送音频数据端使用的协议。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ProfileHandsfreeAudioGateway

```cangjie
ProfileHandsfreeAudioGateway
```

**功能：** HFP Ag Profile，负责通话音频网关使用的协议。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ProfileHidHost

```cangjie
ProfileHidHost
```

**功能：** HID Host Profile，负责与HID Device建立通信并处理数据交互的协议。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ProfilePanNetwork

```cangjie
ProfilePanNetwork
```

**功能：** NAP Profile，负责提供网络共享端使用的协议。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### func !=(ProfileId)

```cangjie
public operator func !=(other: ProfileId): Bool
```

**功能：** 比较两个枚举值是否不相等。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|other|[ProfileId](cj-apis-bluetooth-constant.md#enum-profileid)|是|-|待比较的值。|

**返回值：**

|类型|说明|
|:---|:---|
|Bool|两个枚举值不相同时返回 true，否则返回 false。|

### func ==(ProfileId)

```cangjie
public operator func ==(other: ProfileId): Bool
```

**功能：** 比较两个枚举值是否相等。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|other|[ProfileId](cj-apis-bluetooth-constant.md#enum-profileid)|是|-|待比较的值。|

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

**功能：** 蓝牙设备的主要类型。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**父类型：**

- Equatable\<MajorClass\>
- ToString

### MajorMisc

```cangjie
MajorMisc
```

**功能：** 表示不属于其他标准类别的杂项设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### MajorComputer

```cangjie
MajorComputer
```

**功能：** 表示计算机设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### MajorPhone

```cangjie
MajorPhone
```

**功能：** 表示手机设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### MajorNetworking

```cangjie
MajorNetworking
```

**功能：** 表示局域网/网络接入点设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### MajorAudioVideo

```cangjie
MajorAudioVideo
```

**功能：** 表示音频/视频设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### MajorPeripheral

```cangjie
MajorPeripheral
```

**功能：** 表示外围设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### MajorImaging

```cangjie
MajorImaging
```

**功能：** 表示成像设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### MajorWearable

```cangjie
MajorWearable
```

**功能：** 表示可穿戴设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### MajorToy

```cangjie
MajorToy
```

**功能：** 表示玩具设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### MajorHealth

```cangjie
MajorHealth
```

**功能：** 表示健康设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### MajorUncategorized

```cangjie
MajorUncategorized
```

**功能：** 表示未分类设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### func !=(MajorClass)

```cangjie
public operator func !=(other: MajorClass): Bool
```

**功能：** 比较两个枚举值是否不相等。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|other|[MajorClass](cj-apis-bluetooth-constant.md#enum-majorclass)|是|-|待比较的值。|

**返回值：**

|类型|说明|
|:---|:---|
|Bool|两个枚举值不相同时返回 true，否则返回 false。|

### func ==(MajorClass)

```cangjie
public operator func ==(other: MajorClass): Bool
```

**功能：** 比较两个枚举值是否相等。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|other|[MajorClass](cj-apis-bluetooth-constant.md#enum-majorclass)|是|-|待比较的值。|

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

**功能：** 蓝牙设备的主要和次要组合类型。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**父类型：**

- Equatable\<MajorMinorClass\>
- ToString

### ComputerUncategorized

```cangjie
ComputerUncategorized
```

**功能：** 表示未分类计算机设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ComputerDesktop

```cangjie
ComputerDesktop
```

**功能：** 表示台式计算机设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ComputerServer

```cangjie
ComputerServer
```

**功能：** 表示服务器设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ComputerLaptop

```cangjie
ComputerLaptop
```

**功能：** 表示便携式计算机设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ComputerHandheldPcPda

```cangjie
ComputerHandheldPcPda
```

**功能：** 表示手持式计算机设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ComputerPalmSizePcPda

```cangjie
ComputerPalmSizePcPda
```

**功能：** 表示掌上电脑设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ComputerWearable

```cangjie
ComputerWearable
```

**功能：** 表示可穿戴计算机设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ComputerTablet

```cangjie
ComputerTablet
```

**功能：** 表示平板电脑设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### PhoneUncategorized

```cangjie
PhoneUncategorized
```

**功能：** 表示未分类手机设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### PhoneCellular

```cangjie
PhoneCellular
```

**功能：** 表示便携式手机设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### PhoneCordless

```cangjie
PhoneCordless
```

**功能：** 表示无线电话设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### PhoneSmart

```cangjie
PhoneSmart
```

**功能：** 表示智能手机设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### PhoneModemOrGateway

```cangjie
PhoneModemOrGateway
```

**功能：** 表示调制解调器或网关手机设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### PhoneIsdn

```cangjie
PhoneIsdn
```

**功能：** 表示ISDN手机设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### NetworkFullyAvailable

```cangjie
NetworkFullyAvailable
```

**功能：** 表示网络负载占用率0%的网络设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### Network1To17Utilized

```cangjie
Network1To17Utilized
```

**功能：** 表示网络负载占用率1%~17%的网络设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### Network17To33Utilized

```cangjie
Network17To33Utilized
```

**功能：** 表示网络负载占用率17%~33%的网络设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### Network33To50Utilized

```cangjie
Network33To50Utilized
```

**功能：** 表示网络负载占用率33%~50%的网络设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### Network60To67Utilized

```cangjie
Network60To67Utilized
```

**功能：** 表示网络负载占用率60%~67%的网络设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### Network67To83Utilized

```cangjie
Network67To83Utilized
```

**功能：** 表示网络负载占用率67%~83%的网络设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### Network83To99Utilized

```cangjie
Network83To99Utilized
```

**功能：** 表示网络负载占用率83%~99%的网络设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### NetworkNoService

```cangjie
NetworkNoService
```

**功能：** 表示网络负载占用率100%的网络设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### AudioVideoUncategorized

```cangjie
AudioVideoUncategorized
```

**功能：** 表示未分类音频/视频设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### AudioVideoWearableHeadset

```cangjie
AudioVideoWearableHeadset
```

**功能：** 表示可穿戴式耳机音频/视频设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### AudioVideoHandsfree

```cangjie
AudioVideoHandsfree
```

**功能：** 表示免提音频/视频设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### AudioVideoMicrophone

```cangjie
AudioVideoMicrophone
```

**功能：** 表示麦克风音频/视频设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### AudioVideoLoudspeaker

```cangjie
AudioVideoLoudspeaker
```

**功能：** 表示扬声器音频/视频设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### AudioVideoHeadphones

```cangjie
AudioVideoHeadphones
```

**功能：** 表示头戴式音频/视频设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### AudioVideoPortableAudio

```cangjie
AudioVideoPortableAudio
```

**功能：** 表示便携式音频/视频设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### AudioVideoCarAudio

```cangjie
AudioVideoCarAudio
```

**功能：** 表示汽车音频/视频设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### AudioVideoSetTopBox

```cangjie
AudioVideoSetTopBox
```

**功能：** 表示机顶盒音频/视频设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### AudioVideoHifiAudio

```cangjie
AudioVideoHifiAudio
```

**功能：** 表示高保真音频/视频设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### AudioVideoVcr

```cangjie
AudioVideoVcr
```

**功能：** 表示录像机音频/视频设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### AudioVideoVideoCamera

```cangjie
AudioVideoVideoCamera
```

**功能：** 表示摄像机视频设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### AudioVideoCamcorder

```cangjie
AudioVideoCamcorder
```

**功能：** 表示摄像机音频/视频设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### AudioVideoVideoMonitor

```cangjie
AudioVideoVideoMonitor
```

**功能：** 表示监视器视频设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### AudioVideoVideoDisplayAndLoudspeaker

```cangjie
AudioVideoVideoDisplayAndLoudspeaker
```

**功能：** 表示具备显示和扬声器的视频设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### AudioVideoVideoConferencing

```cangjie
AudioVideoVideoConferencing
```

**功能：** 表示会议视频设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### AudioVideoVideoGamingToy

```cangjie
AudioVideoVideoGamingToy
```

**功能：** 表示游戏玩具视频设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### PeripheralNonKeyboardNonPointing

```cangjie
PeripheralNonKeyboardNonPointing
```

**功能：** 表示非键盘非指向外围设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### PeripheralKeyboard

```cangjie
PeripheralKeyboard
```

**功能：** 表示外围键盘设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### PeripheralPointingDevice

```cangjie
PeripheralPointingDevice
```

**功能：** 表示定点装置外围设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### PeripheralKeyboardPointing

```cangjie
PeripheralKeyboardPointing
```

**功能：** 表示键盘指向外围设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### PeripheralUncategorized

```cangjie
PeripheralUncategorized
```

**功能：** 表示未分类外围设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### PeripheralJoystick

```cangjie
PeripheralJoystick
```

**功能：** 表示外围操纵杆设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### PeripheralGamepad

```cangjie
PeripheralGamepad
```

**功能：** 表示外围游戏板设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### PeripheralRemoteControl

```cangjie
PeripheralRemoteControl
```

**功能：** 表示远程控制外围设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### PeripheralSensingDevice

```cangjie
PeripheralSensingDevice
```

**功能：** 表示外围传感设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### PeripheralDigitizerTablet

```cangjie
PeripheralDigitizerTablet
```

**功能：** 表示外围数字化仪平板电脑设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### PeripheralCardReader

```cangjie
PeripheralCardReader
```

**功能：** 表示外围读卡器设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### PeripheralDigitalPen

```cangjie
PeripheralDigitalPen
```

**功能：** 表示外围数码笔设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### PeripheralScannerRfid

```cangjie
PeripheralScannerRfid
```

**功能：** 表示射频识别扫描仪外围设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### PeripheralGesturalInput

```cangjie
PeripheralGesturalInput
```

**功能：** 表示手势输入外围设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ImagingUncategorized

```cangjie
ImagingUncategorized
```

**功能：** 表示未分类的图像设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ImagingDisplay

```cangjie
ImagingDisplay
```

**功能：** 表示图像显示设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ImagingCamera

```cangjie
ImagingCamera
```

**功能：** 表示成像照相机设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ImagingScanner

```cangjie
ImagingScanner
```

**功能：** 表示成像扫描仪设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ImagingPrinter

```cangjie
ImagingPrinter
```

**功能：** 表示成像打印机设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### WearableUncategorized

```cangjie
WearableUncategorized
```

**功能：** 表示未分类的可穿戴设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### WearableWristWatch

```cangjie
WearableWristWatch
```

**功能：** 表示可穿戴腕表设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### WearablePager

```cangjie
WearablePager
```

**功能：** 表示可穿戴寻呼机设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### WearableJacket

```cangjie
WearableJacket
```

**功能：** 表示可穿戴夹克设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### WearableHelmet

```cangjie
WearableHelmet
```

**功能：** 表示可穿戴头盔设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### WearableGlasses

```cangjie
WearableGlasses
```

**功能：** 表示可穿戴眼镜设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ToyUncategorized

```cangjie
ToyUncategorized
```

**功能：** 表示未分类的玩具设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ToyRobot

```cangjie
ToyRobot
```

**功能：** 表示玩具机器人设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ToyVehicle

```cangjie
ToyVehicle
```

**功能：** 表示玩具车设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ToyDollActionFigure

```cangjie
ToyDollActionFigure
```

**功能：** 表示人形娃娃玩具设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ToyController

```cangjie
ToyController
```

**功能：** 表示玩具控制器设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### ToyGame

```cangjie
ToyGame
```

**功能：** 表示玩具游戏设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### HealthUncategorized

```cangjie
HealthUncategorized
```

**功能：** 表示未分类健康设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### HealthBloodPressure

```cangjie
HealthBloodPressure
```

**功能：** 表示血压健康设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### HealthThermometer

```cangjie
HealthThermometer
```

**功能：** 表示温度计健康设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### HealthWeighing

```cangjie
HealthWeighing
```

**功能：** 表示体重健康设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### HealthGlucose

```cangjie
HealthGlucose
```

**功能：** 表示葡萄糖健康设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### HealthPulseOximeter

```cangjie
HealthPulseOximeter
```

**功能：** 表示脉搏血氧仪健康设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### HealthPulseRate

```cangjie
HealthPulseRate
```

**功能：** 表示脉搏率健康设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### HealthDataDisplay

```cangjie
HealthDataDisplay
```

**功能：** 表示数据显示健康设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### HealthStepCounter

```cangjie
HealthStepCounter
```

**功能：** 表示计步器健康设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### HealthBodyCompositionAnalyzer

```cangjie
HealthBodyCompositionAnalyzer
```

**功能：** 表示身体成分分析仪健康设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### HealthPeakFlowMonitor

```cangjie
HealthPeakFlowMonitor
```

**功能：** 表示峰值流量监控仪健康设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### HealthMedicationMonitor

```cangjie
HealthMedicationMonitor
```

**功能：** 表示药物监视仪健康设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### HealthKneeProsthesis

```cangjie
HealthKneeProsthesis
```

**功能：** 表示膝盖假肢健康设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### HealthAnkleProsthesis

```cangjie
HealthAnkleProsthesis
```

**功能：** 表示脚踝假肢健康设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### HealthGenericHealthManager

```cangjie
HealthGenericHealthManager
```

**功能：** 表示通用健康管理设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### HealthPersonalMobilityDevice

```cangjie
HealthPersonalMobilityDevice
```

**功能：** 表示个人移动健康设备。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

### func !=(MajorMinorClass)

```cangjie
public operator func !=(other: MajorMinorClass): Bool
```

**功能：** 比较两个枚举值是否不相等。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|other|[MajorMinorClass](cj-apis-bluetooth-constant.md#enum-majorminorclass)|是|-|待比较的值。|

**返回值：**

|类型|说明|
|:---|:---|
|Bool|两个枚举值不相同时返回 true，否则返回 false。|

### func ==(MajorMinorClass)

```cangjie
public operator func ==(other: MajorMinorClass): Bool
```

**功能：** 比较两个枚举值是否相等。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**起始版本：** 26.1.0

**参数：**

|参数名|类型|必填|默认值|说明|
|:---|:---|:---|:---|:---|
|other|[MajorMinorClass](cj-apis-bluetooth-constant.md#enum-majorminorclass)|是|-|待比较的值。|

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
