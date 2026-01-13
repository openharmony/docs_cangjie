# Restricted Open Permissions

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

## Application Method

<!--RP1-->

The following permissions are available to normal applications, but require cross-level application through [Access Control List (ACL)](./cj-app-permission-mgmt-overview.md#Basic-Concepts-in-Permission-Mechanism).

Applications at the normal level need to declare their APL level as system_basic or higher. When developing the application installation package, modify the HarmonyAppProvision configuration file (i.e., the `Toolchains / _{Version} _/ lib / UnsgnedReleasedProfileTemplate.json` file in the SDK directory) and re-sign the application.

**Modification Method:**

Example of the HarmonyAppProvision configuration file is shown below. Modify the "apl" field under "bundle-info".

```json
"bundle-info" : {
    // ...
    "apl": "system_basic",
    // ...
},
```

> **Note:**
>
> Direct modification of the HarmonyAppProvision configuration file is only for application debugging and cannot be used for publishing to the app market. For commercial versions of applications, apply for release certificates and Profile files in the corresponding app market.

<!--RP1End-->

## Permission List

### ohos.permission.SYSTEM_FLOAT_WINDOW

Allows applications to use floating window capabilities.

<!--RP25--><!--RP25End-->

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.READ_CONTACTS

Allows applications to read contact data.

<!--RP33--><!--RP33End-->

**Permission Level:** system_basic

**Authorization Method:** User-granted (user_grant)

**Initial Version:** 12

### ohos.permission.WRITE_CONTACTS

Allows applications to add, remove, or modify contact data.

<!--RP34--><!--RP34End-->

**Permission Level:** system_basic

**Authorization Method:** User-granted (user_grant)

**Initial Version:** 12

### ohos.permission.READ_AUDIO

Allows reading audio files from the user's public directory.

<!--RP26--><!--RP26End-->

**Permission Level:** system_basic

**Authorization Method:** User-granted (user_grant)

**Initial Version:** 12

### ohos.permission.WRITE_AUDIO

Allows modifying audio files in the user's public directory.

<!--RP28--><!--RP28End-->

**Permission Level:** system_basic

**Authorization Method:** User-granted (user_grant)

**Initial Version:** 12

### ohos.permission.READ_IMAGEVIDEO

Allows reading image or video files from the user's public directory.

<!--RP27--><!--RP27End-->

**Permission Level:** system_basic

**Authorization Method:** User-granted (user_grant)

**Initial Version:** 12

### ohos.permission.WRITE_IMAGEVIDEO

Allows modifying image or video files in the user's public directory.

<!--RP29--><!--RP29End-->

**Permission Level:** system_basic

**Authorization Method:** User-granted (user_grant)

**Initial Version:** 12

### ohos.permission.READ_WRITE_DESKTOP_DIRECTORY

Allows applications to access the Desktop directory and its subdirectories in the public directory.

<!--RP15-->
Currently, only applications on 2-in-1 devices and tablets can apply for this permission.
<!--RP15End-->

**Permission Level:** system_basic

**Authorization Method:** User-granted (user_grant)

**Initial Version:** 12

### ohos.permission.ACCESS_DDK_USB

Allows extended peripheral drivers to access USB DDK interfaces for developing USB bus extended peripheral drivers.

<!--RP31--><!--RP31End-->

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.ACCESS_DDK_HID

Allows extended peripheral drivers to access HID DDK interfaces for developing HID-class extended peripheral drivers.

<!--RP30--><!--RP30End-->

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.READ_PASTEBOARD

Allows applications to read the clipboard.

<!--RP32--><!--RP32End-->

**Permission Level:** system_basic

**Authorization Method:** User-granted (user_grant)

**Initial Version:** 12

### ohos.permission.FILE_ACCESS_PERSIST

Allows applications to support persistent access to file URIs.

<!--RP18--><!--RP18End-->

**Permission Level:** normal

**Authorization Method:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.INTERCEPT_INPUT_EVENT

Allows applications to intercept input events.

<!--RP24--><!--RP24End-->

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.INPUT_MONITORING

Allows applications to monitor input events.

<!--RP23--><!--RP23End-->

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**Initial Version:** 7

### ohos.permission.SHORT_TERM_WRITE_IMAGEVIDEO

Allows applications to save images or videos to the user's public directory.

After obtaining this permission, applications can receive a short-term authorization of up to 30 minutes to save images/videos. If the time exceeds 30 minutes, a pop-up will reappear, requiring user confirmation again.

<!--RP21--><!--RP21End-->

**Permission Level:** system_basic

**Authorization Method:** User-granted (user_grant)

**Initial Version:** 12

### ohos.permission.READ_WRITE_USER_FILE

Allows applications to access and modify files in the user directory.

<!--RP19-->
Currently, only applications on 2-in-1 devices can apply for this permission.
<!--RP19End-->

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.READ_WRITE_USB_DEV

Allows applications to connect to devices and read/write through USB debugging.

<!--RP20-->
Currently, only applications on 2-in-1 devices can apply for this permission.
<!--RP20End-->

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.GET_WIFI_PEERS_MAC

Allows applications to obtain the MAC addresses of peer Wi-Fi devices.

When obtaining Wi-Fi scan results, this permission is required to retrieve the MAC addresses of peer devices.

<!--RP14--><!--RP14End-->

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**Initial Version:** 12

**Change Information:** In API 12, the permission level was system_core; starting from API 15, the level was changed to system_basic, making it available to normal applications.

### ohos.permission.kernel.DISABLE_CODE_MEMORY_PROTECTION

Allows applications to disable runtime integrity protection for their own code.

<!--RP11-->
For applications developed using cross-platform frameworks, this permission exempts runtime code integrity protection. Currently, only applications on tablets and 2-in-1 devices can apply for this permission.
<!--RP11End-->

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.kernel.ALLOW_WRITABLE_CODE_MEMORY

Allows applications to request writable and executable anonymous memory.

<!--RP10-->
For applications developed using cross-platform frameworks, this permission allows requesting writable and executable anonymous memory. Currently, only applications on tablets and 2-in-1 devices can apply for this permission.
<!--RP10End-->

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.kernel.ALLOW_EXECUTABLE_FORT_MEMORY

Allows the system JS engine to request anonymous executable memory with the MAP_FORT flag.

After obtaining this permission, the system engine can request anonymous executable memory with MAP_FORT for just-in-time compilation, improving formal execution efficiency.

<!--RP13--><!--RP13End-->

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.MANAGE_PASTEBOARD_APP_SHARE_OPTION

Allows applications to set or remove the paste scope of clipboard data.

<!--RP16--><!--RP16End-->

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.MANAGE_UDMF_APP_SHARE_OPTION

Allows applications to set or remove the data sharing scope when using UDMF.

<!--RP17--><!--RP17End-->

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.ACCESS_DISK_PHY_INFO

Allows applications to obtain hardware information about disks.

<!--RP3--><!--RP3End-->

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.PRELOAD_FILE

Allows applications to preload files to improve file opening speed.

<!--RP9--><!--RP9End-->

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.SET_PAC_URL

Allows applications to set the proxy auto-configuration script address.

After configuring the script address, other applications can read and parse this script to determine whether to use a proxy.

<!--RP4--><!--RP4End-->

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.PERSONAL_MANAGE_RESTRICTIONS

Allows device management applications to manage personal device restriction policies.

<!--RP7--><!--RP7End-->

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.START_PROVISIONING_MESSAGE

Allows applications to initiate the device management business deployment process, activating the application as a personal device management application.

<!--RP8--><!--RP8End-->

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.USE_FRAUD_CALL_LOG_PICKER

Allows applications to use the fraud call log picker to obtain call log content.

<!--RP5--><!--RP5End-->

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.USE_FRAUD_MESSAGES_PICKER

Allows applications to use the fraud SMS picker to obtain SMS content.

<!--RP6--><!--RP6End-->

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**Initial Version:** 12### ohos.permission.PERSISTENT_BLUETOOTH_PEERS_MAC

Allows applications to persist the virtual random address corresponding to the MAC address of peer Bluetooth devices.

After obtaining the virtual random address corresponding to the MAC address of peer Bluetooth devices through BLE scanning, BR scanning, or connection monitoring, applications with this permission can maintain this virtual random address for an extended period, unaffected by Bluetooth toggling or rebooting.

<!--RP36--><!--RP36End-->

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.ACCESS_VIRTUAL_SCREEN

Allows applications to manage virtual screens.

Applications with this permission can invoke virtual screen-related interfaces to perform operations such as creating, enabling, and destroying virtual screens.

<!--RP37--><!--RP37End-->

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.MANAGE_APN_SETTING

Allows applications to read or configure APN information.

<!--RP38--><!--RP38End-->

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.GET_WIFI_LOCAL_MAC

Allows applications to retrieve the MAC address of the local Wi-Fi device.

<!--RP43--><!--RP43End-->

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**Initial Version:** 12

**Change History:** From API 12-15, this permission was exclusively available to system applications. Starting from API 16, it is open to regular applications on PC/2-in-1 devices while remaining restricted to system applications on other devices.

### ohos.permission.kernel.ALLOW_USE_JITFORT_INTERFACE

Allows applications to invoke the JITFort interface to update the content of MAP_FORT memory.

<!--RP12--><!--RP12End-->

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.kernel.DISABLE_GOTPLT_RO_PROTECTION

Allows applications to disable read-only protection for the .got.plt section within a process.

<!--RP22--><!--RP22End-->

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.USE_FRAUD_APP_PICKER

Allows applications to use the fraud app picker to retrieve application information.

<!--RP2--><!--RP2End-->

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.kernel.SUPPORT_PLUGIN

Allows host applications to install plugins.

<!--RP35--><!--RP35End-->

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.CUSTOM_SANDBOX

Allows applications to change the sandbox type to dynamic sandbox.

<!--RP39--><!--RP39End-->

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**Initial Version:** 12

### ohos.permission.MANAGE_SCREEN_TIME_GUARD

Allows applications to invoke screen time guard-related interfaces for operations such as screen usage restrictions, application access control, and usage time management.

<!--RP40--><!--RP40End-->

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**Initial Version:** 20

### ohos.permission.CUSTOMIZE_SAVE_BUTTON

Allows applications to customize the icon and text of save controls.

<!--RP41--><!--RP41End-->

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**Supported Devices:** Phone | PC/2-in-1 | Tablet

**Initial Version:** 20

### ohos.permission.GET_ABILITY_INFO

Allows applications to query Ability information based on URIs.

<!--RP42--><!--RP42End-->

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**Supported Devices:** PC/2-in-1

**Initial Version:** 20