# System Application Permissions Available for ACL Application (System Grant)

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

Before applying for target permissions, developers are advised to first understand the [application paths for different permissions](./cj-determine-application-mode.md). After gaining a basic understanding of the permission workflow, refer to the specific descriptions of the following permission fields to determine whether the application can apply for the target permissions, thereby improving development efficiency.

> **Note:**
>
> - The following permissions are only available to applications with an APL level of system_basic or higher, and are not available to applications with an APL level of normal.
> - The grant method for the following permissions is system_grant (system authorization).
> - The following permissions can be applied for across levels via [Access Control List (ACL)](./cj-app-permission-mgmt-overview.md#basic-concepts-in-permission-mechanism).

For the application process, refer to [Choosing the Permission Application Method](./cj-determine-application-mode.md).

## ohos.permission.PRE_START_ATOMIC_SERVICE

Allows the app market to skip the loading dialog and pre-open a window for atomic services, displaying loading animations within the window.

**Permission Level:** system_core

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_APP_KEEP_ALIVE

Allows setting keep-alive for third-party application processes.

**Permission Level:** system_core

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 14

## ohos.permission.ACCESS_BBOX_DIR

Allows system applications to read log files under the bbox path.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.CONTROL_LOCATION_SWITCH

Allows applications to turn the location information switch on and off.

**Permission Level:** system_core

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.LOCATION_SWITCH_IGNORED

Allows system applications to obtain location information even when the location switch is turned off.

**Permission Level:** system_core

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.SUBSCRIBE_SWING_ABILITY

Allows applications to use smart sensing subscription capabilities.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGER_SWING_MOTION

Allows applications to use adaptive air gesture capabilities.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MOCK_LOCATION

Allows applications to use mock location functionality.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_LEARN_MORE_DIALOG

Allows system applications to launch the "Learn More" display dialog to obtain additional details.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 13

## ohos.permission.WRITE_PROTECTION_ADVICE_POLICY

Allows system applications to modify the "Security Advice" database.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 17

## ohos.permission.READ_PROTECTION_ADVICE_POLICY

Allows system applications to read the "Security Advice" database.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 17

## ohos.permission.PROXY_MESSAGE_AUTH

Allows system applications to call the authorization interface of the "Messages" application.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**Initial Version:** 18

## ohos.permission.MANAGE_SETTINGS

Allows applications to set device-level and user-level configuration data tables in SettingsData.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_SCREEN_LOCK

Allows applications to access screen lock information.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ALLOW_UPGRADE_GUIDE_ACCESS

Allows system applications to obtain upgrade guide data for applications or launch upgrade guide components for applications.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_MEDIALIB_THUMB_DB

Allows system applications to access and modify the media library database.

**Permission Level:** system_core

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.AGENT_REQUIRE_FORM

Allows applications to proxy request cards.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_VPN

Allows system applications to start or stop VPN functionality.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

**Change Information:** API 10-11, ACL Enabled is false; starting from API 12, changed to true.

## ohos.permission.WAKEUP_VISION

Allows applications to access the voice assistant visual component.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.WAKEUP_VOICE

Allows applications to access the voice assistant wake-up component.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ATTEST_KEY

Allows applications to obtain a certificate chain for proving the legitimacy of keys.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.GET_PHONE_NUMBERS

Allows applications to read the device's native phone numbers.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACTIVATE_THEME_PACKAGE

Allows system applications to set theme content, including wallpapers, icons, skins, AOD, and fonts.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.QUERY_ACCESSIBILITY_ELEMENT

Allows batch querying of accessibility nodes.

**Permission Level:** system_core

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.SET_UNREMOVABLE_NOTIFICATION

Allows applications to post non-removable notifications.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.UNINSTALL_BUNDLE

Allows applications to uninstall other applications.

**Permission Level:** system_core

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.RECOVER_BUNDLE

Allows recovery of pre-installed applications.

**Permission Level:** system_core

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.UPDATE_SYSTEM

Allows calling upgrade interfaces.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.FACTORY_RESET

Allows calling factory reset interfaces.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ASSIST_DEVICE_UPDATE

Allows launching upgrade services to assist or coordinate upgrades for other devices.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.PLUGIN_UPDATE

Allows business parties to call upgrade-related interfaces to complete post-download and update operations for plugins and AI models.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.RECEIVE_UPDATE_MESSAGE

Allows applications and services to monitor key events during the system upgrade process.

**Permission Level:** system_basic

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.GET_ALL_PROCESSES

Allows system services or system applications to view all files under /proc.

**Permission Level:** system_core

**Grant Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12## ohos.permission.MANAGE_LOCAL_ACCOUNTS

Allows applications to manage system local accounts.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_SYSTEM_SETTINGS

Allows applications to access or launch system settings interfaces.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.SET_ABILITY_CONTROLLER

Allows applications to intercept Ability component startup, primarily for testing and debugging purposes, such as stability robustness testing.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_EXTENSION

Allows applications to interact across system local accounts.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.CLEAN_APPLICATION_DATA

Allows applications to clean application data.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.START_ABILITIES_FROM_BACKGROUND

Allows applications to start or access other components in the background.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_MISSIONS

Allows applications to manage tasks in the system.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_ENTERPRISE_DEVICE_ADMIN

Allows applications to activate device management applications.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ENTERPRISE_CONFIG

Allows applications to activate enterprise devices.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.RECEIVE_ENTERPRISE_POLICY_EVENT

Allows system applications to subscribe to enterprise device management policy events.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 14

## ohos.permission.PUBLISH_SYSTEM_COMMON_EVENT

Allows applications to publish system common events.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.NOTIFICATION_CONTROLLER

Allows applications to manage notifications and subscribe to notifications.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.CLOUDDATA_CONFIG

Allows applications to obtain configuration database cloud-side information capabilities.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.GET_DEFAULT_APPLICATION

Allows applications to query default applications.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_INTELLIGENT_VOICE

Allows applications to access intelligent voice service interfaces.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.POWER_MANAGER

Allows applications to call power management subsystem interfaces to sleep or wake up devices.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.GET_SCENE_CODE

Allows applications to obtain the current scene value of specified applications.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_ECOLOGICAL_RULE

Allows setting scene value generation rules and corresponding experiences for control services.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.INSTALL_ENTERPRISE_BUNDLE

Allows applications to install enterprise InHouse applications.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.INSTALL_BUNDLE

Allows applications to install/uninstall other applications (excluding enterprise-related applications, currently including enterprise InHouse applications, enterprise MDM applications, and enterprise normal applications).

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_SHORTCUTS

Allows applications to query shortcut information of other applications and launch shortcuts of other applications.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.OBSERVE_FORM_RUNNING

Allows applications to monitor card running status.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.WRITE_HIVIEW_SYSTEM

Allows applications to modify hiview data.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.READ_HIVIEW_SYSTEM

Allows applications to access hiview data.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.READ_DFX_SYSEVENT

Allows applications to access system event logging data.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.READ_DFX_XPOWER

Allows applications to access xpower data.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.PERMISSION_USED_STATS

Allows system applications to access permission usage records.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.PERMISSION_RECORD_TOGGLE

Allows applications to set permission usage record switches.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.CAPTURE_SCREEN

Allows applications to capture screen images.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_CERT_MANAGER_INTERNAL

Allows applications to perform operations such as installation, uninstallation, and authorization of user public certificate credentials.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

**Change History:** API 9-11, permission level was system_basic; changed to system_core starting from API 12.

## ohos.permission.CLOUDFILE_SYNC

Allows applications to use cloud synchronization capabilities.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.CHANGE_OVERLAY_ENABLED_STATE

Allows system applications to disable applications with overlay features enabled.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_SCREEN_LOCK_INNER

Allows applications to use screen lock services for locking screens, sending lock screen events, and system event callback functions.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.BACKUP

Allows applications to possess backup and recovery capabilities.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12## ohos.permission.MOUNT_FORMAT_MANAGER

Allows applications to format external storage cards.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MOUNT_UNMOUNT_MANAGER

Allows applications to mount and unmount external storage cards.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.PROXY_AUTHORIZATION_URI

Allows applications to proxy authorization URIs.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_CAST_ENGINE_MIRROR

Allows applications to use screen mirroring capabilities.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_CAST_ENGINE_STREAM

Allows applications to invoke system resource projection capabilities.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.INSTALL_ENTERPRISE_NORMAL_BUNDLE

Allows installation of enterprise normal application packages on enterprise devices.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.UPDATE_MIGRATE

Allows data migration during system upgrades.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_SENSOR

Allows applications to enable/disable sensors without directly using them.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_PRINT_JOB

Allows applications to manage print tasks.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.securityguard.SET_MODEL_STATE

Allows applications to control the device risk management platform model switch.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.UNLOCK_DEVELOPER_MODE

Allows applications to unlock developer mode.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.CAPTURE_VOICE_DOWNLINK_AUDIO

Allows applications to capture downlink voice audio.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.GET_WIFI_INFO_INTERNAL

Allows system processes to obtain Wi-Fi related parameters.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_BUNDLE_DIR

Allows applications to access other applications' installation directories.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.CHANGE_ABILITY_ENABLED_STATE

Allows changing the enabled state of applications or components.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.CLOUDFILE_SYNC_MANAGER

Allows applications to obtain cloud synchronization management capabilities.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.DUMP

Allows exporting system basic information and SA service information.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.DEVICE_STANDBY_EXEMPTION

Allows applications to normally use resources during system standby mode.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.PERCEIVE_SMART_POWER_SCENARIO

Allows applications to perceive smart power consumption scenarios.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_CAMERA_CONFIG

Allows applications to perform operations like global camera toggling.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_AUDIO_CONFIG

Allows applications to perform operations like global microphone muting.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MICROPHONE_CONTROL

Allows applications to perform persistent global microphone muting operations.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.CAPTURE_PLAYBACK

Allows system services to directly record internal audio without using the screen recording framework.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.MICROPHONE_BACKGROUND

Allows system applications to use microphones in the background.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.START_DLP_CRED

Allows system applications or services to launch DLP credential management applications.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.START_SHORTCUT

Allows applications to launch shortcuts.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.PRELOAD_UI_EXTENSION_ABILITY

Pre-launches UIExtensionAbility instances.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_DISPOSED_APP_STATUS

Allows setting and querying application disposal status.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.GET_DISPOSED_APP_STATUS

Allows querying application disposal status.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.FILE_ACCESS_MANAGER

Allows file management applications to access public data files through the FAF framework.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_PUSH_SERVICE

Allows applications to access push service Abilities.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_NET_STRATEGY

Allows applications to obtain network strategy information or modify network strategy settings.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.securityguard.REQUEST_SECURITY_EVENT_INFO

Allows applications to obtain detailed risk data.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.securityguard.REPORT_SECURITY_INFO

Allows applications to report risk data to the device risk management platform.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12```markdown
## ohos.permission.GET_SENSITIVE_PERMISSIONS

Allows an application to read the status of sensitive permissions of other applications.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**Supported Devices:** General

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_SERVICE_DM

Allows system applications to obtain the authentication and networking capabilities of distributed devices.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.UPLOAD_SESSION_MANAGER

Allows an application to manage upload task sessions.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ABILITY_BACKGROUND_COMMUNICATION

Allows an application to launch an Ability component in the background and establish a communication connection with it.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_DLP_FILE

Allows permission configuration and management for DLP files.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_IDS

Allows an application to query unique identifier information of the device.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_MISSIONS

Allows an application to access task stack information.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

**Deprecated Version:** 9

## ohos.permission.BUNDLE_ACTIVE_INFO

Allows system applications to query the runtime information of other applications in the foreground or background.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.CONNECT_IME_ABILITY

Allows binding to the InputMethodAbility.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.CONNECT_SCREEN_SAVER_ABILITY

Allows binding to the ScreenSaverAbility.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.CONNECTIVITY_INTERNAL

Allows applications to obtain network-related information or modify network-related settings. Currently, only system applications can request this permission.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.CONTROL_TASK_SYNC_ANIMATOR

Allows an application to use synchronized task animations.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.DOWNLOAD_SESSION_MANAGER

Allows an application to manage download task sessions.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.GET_DISTRIBUTED_ACCOUNTS

Allows an application to query system distributed account information.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.GET_LOCAL_ACCOUNTS

Allows an application to query system local account information.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.GET_TELEPHONY_STATE

Allows an application to read telephony information.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_BOOSTER_SERVICE

Allows system services or system applications to invoke functional interfaces in the network booster service, such as network quality awareness, network scenario prediction, and network acceleration.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.GET_WALLPAPER

Allows an application to read wallpaper files.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.GRANT_SENSITIVE_PERMISSIONS

Allows an application to grant sensitive permissions to other applications.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**Supported Devices:** General

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.LAUNCH_DATA_PRIVACY_CENTER

Allows an application to navigate from its privacy statement page to the "Data & Privacy" page.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.LISTEN_BUNDLE_CHANGE

Allows an application to monitor changes in the installation, update, or uninstallation status of other applications.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_BLUETOOTH

Allows an application to pair with Bluetooth devices and access their phonebooks or messages.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS

Allows an application to manage system distributed account information.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_MEDIA_RESOURCES

Allows an application to obtain and manage media resources currently being played on the device.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_SECURE_SETTINGS

Allows an application to modify security-related system settings.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_WIFI_CONNECTION

Allows an application to manage Wi-Fi connections.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_WIFI_HOTSPOT

Allows an application to enable or disable Wi-Fi hotspots.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.NOTIFICATION_AGENT_CONTROLLER

Allows an application to send proxy notifications.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.PLACE_CALL

Allows an application to place phone calls directly.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.POWER_OPTIMIZATION

Allows system applications to configure power-saving modes, obtain power-saving mode settings, and receive notifications of configuration changes.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.PROVISIONING_MESSAGE

Allows activation of the super device manager application.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.radio.ACCESS_FM_AM

Allows an application to access FM/AM radio-related services.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.READ_SCREEN_SAVER

Allows an application to query screen saver status information.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12
```## ohos.permission.REBOOT

Allows applications to reboot the device.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.REBOOT_RECOVERY

Allows system applications to reboot the device into recovery mode.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.REFRESH_USER_ACTION

Allows applications to recalculate timeout periods upon receiving user events.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.REMOVE_CACHE_FILES

Allows clearing cache files of specified applications.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.REQUIRE_FORM

Allows applications to obtain Ability Forms.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.START_DESKTOP_UI_COMPONENT

Allows applications to launch desktop UI components.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.REVOKE_SENSITIVE_PERMISSIONS

Allows applications to revoke sensitive permissions granted to other applications.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**Supported Devices:** General

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.RUN_ANY_CODE

Allows applications to execute unsigned code.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.sec.ACCESS_UDID

Allows system applications to retrieve UDID.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.securityguard.REQUEST_SECURITY_MODEL_RESULT

Allows applications to obtain device risk status.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.SET_DEFAULT_APPLICATION

Allows applications to set or reset default applications.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.SET_TELEPHONY_STATE

Allows applications to modify telephony states.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.SET_TIME

Allows applications to modify system time.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.SET_TIME_ZONE

Allows applications to modify system time zones.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.START_ABILIIES_FROM_BACKGROUND

Allows applications to launch FAs (Feature Abilities) in the background.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

**Deprecated Version:** 9

## ohos.permission.START_INVISIBLE_ABILITY

Allows applications to invoke Abilities regardless of their visibility.

**Permission Level:** system_core

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.STORAGE_MANAGER

Allows applications to call storage manager service interfaces for space statistics and volume information queries.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.UPDATE_CONFIGURATION

Allows updating system configurations.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.WRITE_SCREEN_SAVER

Allows applications to modify screensaver status information.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.GET_BLUETOOTH_LOCAL_MAC

Allows applications to retrieve the local Bluetooth MAC address.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.GET_BLUETOOTH_PEERS_MAC

Allows applications to retrieve the real Bluetooth MAC addresses of peripheral devices.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.USE_USER_IDM

Allows applications to access system identity credential information.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_USER_IDM

Allows enrollment and management of user identity authentication credentials.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_PIN_AUTH

Allows registration of callback functions to obtain PIN data during password authentication processes.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_USER_AUTH_INTERNAL

Allows invocation of internal interfaces of the unified identity authentication service.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.SUPPORT_USER_AUTH

Access permission for the unified user authentication control resource pool.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_SENSING_WITH_ULTRASOUND

Allows applications to utilize ultrasonic sensing.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_DISTRIBUTED_HARDWARE

Allows system services or system applications to access distributed hardware resources.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.INSTANTSHARE_SWITCH_CONTROL

Allows system services or system applications to modify instant sharing switch states.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_INSTANTSHARE_SERVICE

Allows system services or system applications to access instant sharing services.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_INSTANTSHARE_PRIVATE_ABILITY

Allows system services or system applications to utilize private application capabilities of instant sharing.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_MCP_AUTHORIZATION

Allows MCP host applications to proxy sub-applications for user account authorization login.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.GET_BUNDLE_RESOURCES

Allows querying application resource information.

**Permission Level:** system_basic

**Authorization Mode:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12## ohos.permission.COOPERATE_MANAGER

Allows system applications to enable cross-device keyboard and mouse sharing capabilities.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.PERCEIVE_TRAIL

Allows system applications to use MSDP footprint perception functionality.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.EXECUTE_INSIGHT_INTENT

Allows system applications to execute intent calls.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.VERIFY_ACTIVATION_LOCK

Allows applications to verify the validity of activation lock credentials.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_OUC

Allows system applications to initiate software update capabilities.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_FINGERPRINT_AUTH

Allows calling interfaces for configuring and managing fingerprint authentication modules.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.TRUSTED_RING_HASH_DATA_PERMISSION

Allows applications to send data to critical asset trusted rings.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.INPUT_CONTROL_DISPATCHING

Allows system applications to block shortcut key distribution logic.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_TRUSTED_RING

Allows the use of capabilities provided by critical asset trusted ring services.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.USE_TRUSTED_RING

Allows applications or services to utilize critical asset trusted ring joining capabilities.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.RECEIVE_APP_INSTALL_INFO_CHANGE

Allows applications to monitor the installation progress of other applications.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.LAUNCH_SPAMSHIELD_PAGE

Allows applications to access spam blocking pages.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_SPAMSHIELD_SERVICE

Allows applications to access spam blocking capabilities.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_SECURITY_PRIVACY_CENTER

Allows services to integrate with the Security and Privacy Center.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.GET_SECURITY_PRIVACY_ADVICE

Allows system applications to obtain recommendation-related data from the Security and Privacy Center.

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.SET_SECURITY_PRIVACY_ADVICE

Allows system applications to process protection recommendations from the Security and Privacy Center.

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.USE_SECURITY_PRIVACY_MESSAGER

Allows system services to call permission management-related interfaces.

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.GET_PRIVACY_INDICATOR

Allows system applications to obtain detailed information about privacy permission event notifications.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.SET_PRIVACY_INDICATOR

Allows system applications to control the display status of privacy permission event notifications.

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.EXEMPT_PRIVACY_INDICATOR

Allows applications to suppress notifications when using permissions.

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.EXEMPT_CAMERA_PRIVACY_INDICATOR

Allows applications to suppress camera permission usage notifications.

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.EXEMPT_MICROPHONE_PRIVACY_INDICATOR

Allows applications to suppress microphone permission usage notifications.

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.EXEMPT_LOCATION_PRIVACY_INDICATOR

Allows applications to suppress location permission usage notifications.

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.EXEMPT_PRIVACY_SECURITY_CENTER

Allows system applications to hide from the permission details page in "Privacy and Security".

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 13

## ohos.permission.GET_SUPER_PRIVACY

Allows retrieval of the super privacy mode status.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.SET_SUPER_PRIVACY

Allows configuration of the super privacy mode status.

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_PRIVATE_SPACE_MANAGER

Allows system applications or services to launch private space management.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_PRIVATE_SPACE_PASSWORD_PROTECT

Allows system applications to call password protection-related interfaces of private space services.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_PASSWORDVAULT_ABILITY

Allows system applications or services to launch password vault capabilities.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_TEXTAUTOFILL_ABILITY

Allows system applications or services to launch text autofill application management pages.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_LOWPOWER_MANAGER

Allows system applications or services to send messages to lowpowermanager.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_APP_BOOT

Allows system applications to configure auto-start settings for other applications during boot.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_ACCOUNT_KIT_SERVICE

Allows account services to query and modify account data.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.REQUEST_ANONYMOUS_ATTEST

Allows system applications to use device anonymous attestation capabilities.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12## ohos.permission.ACCESS_ACCOUNT_KIT_UI

Allows system applications to launch the account user authentication interface.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.START_RECENT_ABILITY

Allows applications to launch a specified UIAbility. If the UIAbility has multiple instances, the most recently launched instance will be started.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.MANAGE_CLOUD_SYNC_CONFIG

Allows applications integrated with cloud storage to manage cloud synchronization configurations.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.ACCESS_FINDDEVICE

Allows applications to launch the "Find Device" application.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.MANAGE_FINDSERVICE

Allows system applications to retrieve the status of the "Find My Device" toggle and enable it.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.READ_FINDSERVICE

Allows system applications to read the status of the "Find My Device" toggle.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.MANAGE_USB_CONFIG

Allows applications to manage USB device functionalities and ports.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.START_SYSTEM_DIALOG

Allows applications to launch system modal dialogs.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.ACCESS_STATUSBAR_ICON

Allows applications to access status bar icons.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** TRUE

**Since Version:** 12

## ohos.permission.MANAGE_SYSTEM_AUDIO_EFFECTS

Allows applications to manage system audio effects.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.SECURE_PASTE

Allows applications to silently read clipboard content.

**Permission Level:** system_core

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.SET_CODE_PROTECT_INFO

Allows system applications to configure cloud-side public keys and encrypted work keys, and negotiate code protection key information.

**Permission Level:** system_core

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.SET_ADVANCED_SECURITY_MODE

Allows applications to modify the configuration of Shield Protection Mode.

**Permission Level:** system_core

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.SET_DEVELOPER_MODE

Allows applications to modify developer mode configurations.

**Permission Level:** system_core

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.DISABLE_PERMISSION_DIALOG

Allows system applications to configure whether specified applications can launch permission dialogs.

**Permission Level:** system_core

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.MANAGE_ACTIVATION_LOCK

Allows applications to manage device activation locks.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.MANAGE_PRIVATE_PHOTOS

Allows applications to access system-preset hidden albums and their contents.

**Permission Level:** system_core

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.RECORD_VOICE_CALL

Allows applications to record call content.

**Permission Level:** system_core

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.MANAGE_APP_INSTALL_INFO

Allows applications to create and manage application installation tasks.

**Permission Level:** system_core

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.MANAGE_APP_UNINSTALL

Allows system applications to uninstall other applications.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 19

## ohos.permission.ACCESS_ADVANCED_SECURITY_MODE

Allows system applications to open the Shield Protection Mode configuration interface.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.ACCESS_HIVIEWX

Allows system applications to launch the "User Experience Improvement Program".

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.ACCESS_HIVIEWCARE

Allows system applications to launch intelligent detection capabilities.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.SET_SANDBOX_POLICY

Allows system applications to configure dynamic sandbox policies.

**Permission Level:** system_core

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.CHECK_SANDBOX_POLICY

Allows system applications or services to query sandbox control policies of other applications.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 15

## ohos.permission.TRIGGER_ACTIVATIONLOCK

Allows system SAs to invoke "Find Device".

**Permission Level:** system_core

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.WRITE_PRIVACY_PUSH_DATA

Allows applications to write privacy Push data into another application.

**Permission Level:** system_core

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.READ_PRIVACY_PUSH_DATA

Allows applications to read Push privacy data from another application.

**Permission Level:** system_core

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.MANAGE_NEARLINK

Allows applications to pair NearLink devices and access their phonebooks or messages.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.GET_NEARLINK_LOCAL_MAC

Allows applications to retrieve the local NearLink MAC address.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.GET_NEARLINK_PEER_MAC

Allows applications to retrieve the NearLink MAC address of peer devices.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.MANAGE_UWB

Allows system applications to manage UWB functionalities.

For example: enabling/disabling UWB, querying chip types, and checking UWB capabilities.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12

## ohos.permission.USE_UWB_RANGING

Allows system applications to use UWB ranging functionalities.

For example: opening ranging sessions, starting/stopping ranging, and closing ranging sessions.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Since Version:** 12## ohos.permission.MANAGE_FINDNETWORK

Allows applications to manage the "Find" network switch and perform pairing/unpairing operations on items.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.OPERATE_FINDNETWORK

Allows applications to invoke "Find" network operation interfaces.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.QUERY_FINDNETWORK_LOCATION

Allows applications to use the "Find" network to query offline device locations.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.REGISTER_FINDNETWORK_ACCESSORY

Allows applications and system services to initiate the Find network accessory registration process.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 13

## ohos.permission.MANAGE_SHUTDOWN_FINDNETWORK

Allows applications and system services to manage device shutdown find functionality.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 15

## ohos.permission.MANAGE_RGM

Allows system services or system applications to manage RGM.

**Permission Level:** system_core

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_PROTOCOL_DFX_DATA

Allows system applications to read communication failure and system statistical data.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_PROTOCOL_DFX_STATE

Allows system applications to enable or disable communication protocol-related switches.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_CMAP_SERVICE

Allows system applications to access communication map services.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 14

## ohos.permission.MANAGE_USER_ACCOUNT_INFO

Allows system applications and system SAs to invoke account services.

**Permission Level:** system_core

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ALLOW_TIPS_ACCESS

Allows system applications to launch externally exposed components of other system applications.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_AI_ABILITY

Allows applications and system SAs to invoke interfaces of voice and vision services.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.READ_HEALTH_MOTION

Allows system applications to read step count and three-ring activity information.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.hsdr.REQUEST_HSDR

Allows system applications to access the security policy cloud query functionality of the security detection response framework.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.WRITE_GTOKEN_POLICY

Allows system applications to write application control policies.

**Permission Level:** system_core

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.READ_GTOKEN_POLICY

Allows system applications to read application control policies.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.NOTIFY_DEBUG_ASSERT_RESULT

Allows applications to set debug assertion results.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.QUERY_PASSWORD_VAULT_DATA

Allows applications to retrieve password vault account data.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.WRITE_ACCOUNT_LOGIN_STATE

Allows user accounts to write their login status to data management services.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_AS_USER

Allows U0 user space services to invoke account open capability APIs.

**Permission Level:** system_core

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.SUBSCRIBE_NOTIFICATION_WINDOW_STATE

Allows applications to subscribe to broadcasts sent when the notification panel is displayed or collapsed.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.CHANGE_DISPLAYMODE

Allows system applications to change screen modes.

**Permission Level:** system_core

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MIGRATE_DATA

Allows applications to migrate data from the input path to a specified directory.

**Permission Level:** system_core

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_DYNAMIC_ICON

Allows applications to use dynamic icons.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.CHANGE_BUNDLE_UNINSTALL_STATE

Allows system applications to change the uninstallable state of specified applications.

**Permission Level:** system_core

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_STYLUS_EVENT

Allows system applications to use stylus system capabilities.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.USE_CLOUD_DRIVE_SERVICE

Allows applications and services to use cloud drive services for device-cloud data synchronization.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** TRUE

**Initial Version:** 12

## ohos.permission.USE_CLOUD_BACKUP_SERVICE

Allows applications and services to trigger cloud backup task execution and notify backup-related events.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** TRUE

**Initial Version:** 12

## ohos.permission.USE_CLOUD_COMMON_SERVICE

Allows applications to obtain cloud-related information and resources through cloud common services.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** TRUE

**Initial Version:** 12

## ohos.permission.PRELOAD_APPLICATION

Allows system applications or system services to preload application processes.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ENABLE_EXPERIENCE_HBM

Allows applications to enable screen HBM (High Brightness Mode).

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 13

## ohos.permission.SET_PROCESS_CACHE_STATE

Allows applications to configure whether to support application caching and fast startup after caching.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_SYSTEM_APP_CERT

Allows callers to manage and use system business certificate credentials.

**Permission Level:** system_core

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_USER_TRUSTED_CERT

Allows callers to manage user CA certificates.

**Permission Level:** system_core

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12## ohos.permission.ACCESS_LOCAL_BACKUP

Allows applications to access local backup data directories.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.CAST_AUDIO_OUTPUT

Allows system casting/collaboration applications to initiate audio casting.

**Permission Level:** system_core

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.WRITE_RINGTONE

Allows write operations to the ringtone library.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.GET_ACCOUNT_MINORS_INFO

Allows system applications to obtain minor user account information.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_LOCAL_THEME

Allows system applications to access locally downloaded theme content.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_SHADER_CACHE_DIR

Allows system applications to access the shader_cache main directory.

**Permission Level:** system_core

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.INSTALL_CLONE_BUNDLE

Allows applications to install application clones.

**Permission Level:** system_core

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.UNINSTALL_CLONE_BUNDLE

Allows applications to uninstall application clones.

**Permission Level:** system_core

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_SCREEN_LOCK_MEDIA_DATA

Allows applications to continue accessing media image and video data after screen lock.

**Permission Level:** system_core

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_SCREEN_LOCK_ALL_DATA

Allows applications to continue accessing sensitive data including media images/videos, call logs, call recordings, SMS content, emails, etc. after screen lock.

**Permission Level:** system_core

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_DEVICE_COLLABORATION_PRIVATE_ABILITY

Allows system services or system applications to access multi-screen collaboration private application capabilities.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_FILE_CONTENT_SHARE

Allows system services or system applications to access shared file content.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_RINGTONE_RESOURCE

Allows system applications to access and write to public ringtone data directories.

**Permission Level:** system_core

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_SUBSCRIPTION_CAPSULE_DATA

Allows system applications to access subscription capsule data.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_SEARCH_SERVICE

Allows system applications to invoke local search capabilities provided by the integrated search service.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.INJECT_INPUT_EVENT

Allows system applications to inject input events.

**Permission Level:** system_core

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.QUERY_SECURITY_EVENT

Allows applications to obtain detailed risk data.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.REPORT_SECURITY_EVENT

Allows applications to report risk data to the device risk management platform.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.QUERY_SECURITY_MODEL_RESULT

Allows applications to query security model execution results.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_SECURITY_GUARD_CONFIG

Allows applications to manage configurations of device risk management components.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.COLLECT_SECURITY_EVENT

Allows applications to collect security events.

**Permission Level:** system_core

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.QUERY_SECURITY_POLICY_FROM_CLOUD

Allows applications to query security policies from the cloud.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.REPORT_SECURITY_EVENT_TO_CLOUD

Allows applications to report security events to the cloud.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_SCAN_SERVICE

Allows system applications to invoke barcode value distribution capabilities provided by the scan-to-access service.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_FACTORY_OTA_DIR

Allows system applications to access wireless update directories.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_MOUSE_CURSOR

Allows system applications to configure mouse cursor related states.

**Permission Level:** system_core

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.FILTER_INPUT_EVENT

Allows system applications to filter input events.

**Permission Level:** system_core

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.INPUT_DEVICE_CONTROLLER

Allows applications to query and configure input device related states.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.ACTIVATE_DEVICE_PSI

Allows system applications or services to report device activation status.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.DUMP_AUDIO

Allows applications to enable audio framework dump capability, storing audio data locally.

**Permission Level:** system_core

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.RECEIVE_FUSION_MESSAGES

Allows system services or applications to receive fusion service messages.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.RECEIVE_BMS_BROKER_MESSAGES

Allows system services or applications to receive package management broker service messages.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.ACCESS_FUSION_MANAGER

Allows system services or applications to access fusion services.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.PUBLISH_LOCATION_EVENT

Allows applications to publish public events related to location management.

**Permission Level:** system_basic

**Authorization Method:** System-granted (system_grant)

**ACL Enabled:** true

**Initial Version:** 12```markdown
## ohos.permission.ACCESS_MULTICORE_HYBRID_ABILITY

Allows applications to access smartwatch system services.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_DEVICE_COLLABORATION_SERVICE

Allows applications to use multi-screen service capabilities.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.GET_APP_DOMAIN_BUNDLE_INFO

Allows applications to access the mapping relationship between applications and domains.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.OPEN_FILE

Allows system applications to launch file management applications and open files/folders.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.PROCESS_FILE_COPY_PASTE

Allows system applications to launch file management applications and perform file copy, cut, and paste operations.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.CLEAR_RECYCLEBIN

Allows system applications to launch file management applications and empty the recycle bin.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.GET_FILE_THUMBNAIL

Allows system services to obtain file thumbnails.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.NETWORK_DHCP

Allows system applications to request IP addresses from DHCP and allocate IP addresses.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ALLOW_CONNECT_CAR

Allows applications to connect to vehicle infotainment systems.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_IDM_WIDGET

Allows system applications to launch credential input widgets.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.MANAGE_ACCESSORY

Allows applications to obtain accessory (keyboard, mouse, etc.) information, send data to accessories, and receive responses.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.COLLECT_ACCESSORY_LOG

Allows applications to collect accessory (keyboard, mouse, etc.) logs.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.INSTALL_INTERNALTESTING_BUNDLE

Allows applications to install developer beta builds.

**Permission Level:** system_core

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.PUBLISH_DISPLAY_ROTATION_EVENT

Allows SAs to send screen rotation status information to applications or system services.

**Permission Level:** system_core

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.PUBLISH_CAST_PLUGGED_EVENT

Allows SAs to send screen casting cable insertion/removal status information to applications or system services.

**Permission Level:** system_core

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.GET_ETHERNET_LOCAL_MAC

Allows applications to query the current MAC address of Ethernet.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 13

## ohos.permission.ALLOW_SHOW_NON_SECURE_WINDOWS

Allows modal UIExtension to unhide non-secure windows.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.ACCESS_DISTRIBUTED_MODEM

Allows system services to access virtual modems.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 13

## ohos.permission.GET_TELEPHONY_ESIM_STATE

Allows system applications to obtain eSIM profile information and device chip provisioning attributes.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 14

## ohos.permission.SET_TELEPHONY_ESIM_STATE

Allows system applications to modify eSIM profile files and perform eSIM upgrades.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 14

## ohos.permission.CAMERA_BACKGROUND

Allows system applications to use the camera in the background.

**Permission Level:** system_core

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 13

## ohos.permission.CALLED_TRANSITION_ON_LOCK_SCREEN

Allows applications to be launched and directly transitioned by other applications on the lock screen.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 13

## ohos.permission.CALLED_BELOW_LOCK_SCREEN

Allows applications to be launched while the device is locked.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 13

## ohos.permission.ACCESS_ANALYTICS

Allows system services to access and read contents under /data/log/faultlog/faultlogger.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.START_RESTORE_NOTIFICATION

Allows system applications to subscribe to backup framework restoration events.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 13

## ohos.permission.READ_WEATHER_DATA

Allows applications to read weather data.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 14

## ohos.permission.ACCESS_MCU_LOG_DIR

Allows system applications to access MCU (microcontroller unit) log directories.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.GRANT_SHORT_TERM_WRITE_MEDIAVIDEO

Allows system applications or services to grant third-party applications temporary access for storing images and videos.

**Permission Level:** system_core

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.CHECK_QUICKFIX_RESULT

Allows system services or applications to check patch installation results.

**Permission Level:** system_core

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 12

**Change History:** APIs 12-13: Available to system services only; From API 14: Available to system applications.

## ohos.permission.USER_AUTH_FROM_BACKGROUND

Allows applications/services to initiate user authentication requests in the background.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 13

## ohos.permission.MANAGE_RECOVERY_KEY

Allows applications to create or delete recovery keys.

**Permission Level:** system_core

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 14

## ohos.permission.UTILIZE_RECOVERY_KEY

Allows applications to use recovery keys to reset lock screen passwords or restore user data.

**Permission Level:** system_core

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 14

## ohos.permission.ACCESS_CONFIDENTIAL_COMPUTING_ZONE

Allows applications to access confidential computing zones.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.SYNC_ASSET_BETWEEN_TRUSTED_ACCOUNT

Allows applications to synchronize critical assets between devices logged in with the same trusted account.

**Permission Level:** system_basic

**Authorization Method:** System grant (system_grant)

**ACL Enabled:** true

**Initial Version:** 18
```## ohos.permission.GET_RECOVERY_KEY_BRIEF_INFORMATION

Allows applications to retrieve brief information about recovery keys.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 14

## ohos.permission.ACCESS_VIRTUAL_KEYBOARD

Allows applications/services to update/query virtual keyboard status.

With this permission, applications can update virtual keyboard status, and services can query virtual keyboard status. Currently, this permission is only available for 2-in-1 device scenarios.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 14

## ohos.permission.READ_APP_LOCK

Allows system applications to read app lock status.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 13

## ohos.permission.WRITE_APP_LOCK

Allows system applications to modify app lock status.

**Permission Level:** system_core

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 13

## ohos.permission.ACCESS_APP_LOCK

Allows applications to access app lock.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 13

## ohos.permission.ACCESS_APP_SINGLE_PERMISSION_MANAGEMENT

Allows applications to launch interfaces for modifying other applications' authorization settings.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 15

## ohos.permission.ACCESS_APP_INSTALL_DIR

Allows system applications to access installation file directories.

**Permission Level:** system_core

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 14

## ohos.permission.ACCESS_ACCOUNT_SERVICE_EXTENSION_ABILITY

Allows system applications to invoke services provided by Account ServiceExtensionAbility.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 15

## ohos.permission.ANTI_FRAUD

Allows applications to integrate risk control probes for device-side risk detection, with results serving as input for cloud-side risk decision-making.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.EXEMPT_CAPTURE_SCREEN_AUTHORIZE

Allows applications to initiate screen recording without displaying privacy authorization pop-ups.

**Permission Level:** system_core

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 15

## ohos.permission.STORAGE_MANAGER_CRYPT

Allows system applications and services to call interfaces for encryption/decryption operations.

**Permission Level:** system_core

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

## ohos.permission.WATCH_READ_EMERGENCY_INFO

Allows applications to read SOS personal emergency information data.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.WATCH_WRITE_EMERGENCY_INFO

Allows applications to write SOS personal emergency information data.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.WATCH_START_SOS_SERVICE

Allows applications to enable or access SOS services.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

**Change History:** For APIs 12-14, this permission was only available to system services; starting from API 15, it became available to system applications.

## ohos.permission.ACCESS_DLP_HIDE_INFO

Allows system applications to launch anti-peeping protection settings pages.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.DLP_GET_HIDE_STATUS

Allows system applications to use information hiding interfaces and obtain information hiding status.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.GET_ANIM_POLICY

Allows system applications to register animation plugins and obtain animation usage policies.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.VIRTUAL_KEYBOARD_WINDOW

Allows system applications to create virtual keyboard windows.

System applications must obtain this permission to successfully create virtual keyboard windows. Currently, only 2-in-1 device system applications can apply for this permission.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 15

## ohos.permission.GET_FAMILY_INFO

Allows system applications to retrieve group information from "Family Sharing".

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.ACCESS_FUSION_AWARENESS_DATA

Allows system applications to obtain fusion awareness data.

**Permission Level:** system_core

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.ACCESS_ACCOUNT_RECOMMENDATION_DATA

Allows applications to read "Account Recommendation" data and launch Account Recommendation List UIExtensionAbility.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.GET_PAGE_INFO

Allows system applications to obtain specified application page information.

**Permission Level:** system_core

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.ACCESS_DDK_DRIVERS

Allows extended peripheral driver clients to bind to extended peripheral driver servers.

This permission verifies binding between extended peripheral clients and servers with the following rules:

1. The target extended driver server described in the peripheral extension driver client's permission declaration must be already published or published together.
2. The capabilities provided by the target extended driver server must match the business requirements of the peripheral extension driver client.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Carries Additional Data:** Yes

**Initial Version:** 18

## ohos.permission.ACCESS_DDK_SCSI_PERIPHERAL

Allows extended peripheral drivers to access SCSI DDK interfaces for developing SCSI Peripheral extended peripheral drivers.

Supports development of peripheral extension drivers meeting these conditions:
Peripherals connected via USB bus that satisfy:

1. Peripheral InterfaceClass is Mass Storage (0x08), InterfaceSubClass is SCSI transparent command set (0x06).
2. Peripherals can emulate SCSI devices transparently to the operating system.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.ACCESS_DDK_USB_SERIAL

Allows extended peripheral drivers to access USBSerial DDK interfaces for developing USB Serial extended peripheral drivers.

Supports development of peripheral extension drivers meeting these conditions:
Peripherals connected via USB bus that satisfy:

1. Peripheral InterfaceClass is Communication Device Class (0x02), InterfaceSubClass follows ACMSubClass model (0x02).
2. Peripherals support emulating traditional serial communication via USB interfaces.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.ACCESS_CUSTOM_RINGTONE

Allows applications to access the ringtone library.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.ACCESS_STARTUPGUIDE

Allows system applications to access normal data and common public events of the startup wizard application.

Only mobile, tablet, and 2-in-1 device applications can apply for this permission.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.ACCESS_DEVAUTH_CRED_MGR

Allows system applications or services to access the credential management module of the Device Mutual Trust Authentication SA.

**Permission Level:** system_core

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.ACCESS_DEVAUTH_CRED_PRIVILEGE

Allows system applications or services to access both credential management and authentication modules of the Device Mutual Trust Authentication SA, enabling query and authentication of other business credentials.

**Permission Level:** system_core

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.ACCESS_DEVAUTH_CRED_AUTH

Allows system applications or services to access the credential authentication module of the Device Mutual Trust Authentication SA.

**Permission Level:** system_core

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.ANTIFRAUD_DETECT

Allows system applications to perform anti-fraud detection.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.ANTIFRAUD_PICTURE_DETECT

Allows system applications to perform face-swapping detection in images.

**Permission Level:** system_basic

**Grant Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18## ohos.permission.ANTIFRAUD_MODEL_DOWNLOAD

Allows system applications to use model download-related interfaces.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.ACCESS_APP_CLONE_DIR

Allows system applications to access installation file paths copied from other devices.

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.ACCESS_MEDIALIB_RESTORE

Allows applications to mount media recovery paths.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 17

## ohos.permission.ACCESS_TRUST_LIST_OOBE_MANAGER

Allows applications to manage the list of applications that can be launched during the out-of-box experience (OOBE).

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.GET_NETWORK_STATS

Allows system applications to obtain historical network traffic data.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 12

**Change History:** For API 10-11, ACL was disabled (false); Starting from API 12, changed to true.

## ohos.permission.READ_DLP_HIDE_SWITCH

Allows system applications to read data from the screen peek prompt database.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.WRITE_DLP_HIDE_SWITCH

Allows system applications to write data to the screen peek prompt database.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.INSTALL_PLUGIN_BUNDLE

Allows applications to call plugin installation interfaces.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 19

## ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

Allows applications to call interfaces for accessing DLP files in enterprise workspaces.

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Supported Devices:** PC/2in1

**Initial Version:** 20

## ohos.permission.UNINSTALL_PLUGIN_BUNDLE

Allows applications to call plugin uninstallation interfaces.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 19

## ohos.permission.GET_EDM_CONFIG

Allows system applications to view industry-customized configuration files.

Used to protect the visibility of industry-customized configurations, such as boot animations, boot logos, desktop layouts, wallpapers, etc.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.READ_DHA

Allows applications to read device health attestation information.

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.WRITE_DHA

Allows applications to write device health attestation information.

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.NOTIFY_DHA

Allows applications to notify device health attestation events.

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.CHANGE_DEFAULT_APPLICATION

Allows applications to monitor "default application" change events.

Users can set "default applications" in system settings, such as designating a default app for opening specific file types. When the "default application" changes, a corresponding event will be triggered.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 19

## ohos.permission.SEND_NOTIFICATION_CROSS_USER

Allows applications to send notifications to specified users in the system.

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

## ohos.permission.ALLOW_ACCESS_TIPS

Allows system applications to launch components provided by Tips.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 18

### ohos.permission.UPDATE_FONT

Allows applications to install and uninstall fonts.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 19

## ohos.permission.ACCESSIBILITY_EXTENSION_ABILITY

Allows applications to query and manipulate UI components through accessibility service interfaces.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**Supported Devices:** General

**ACL Enabled:** true

**Initial Version:** 20

## ohos.permission.READ_SOUND_RECORD_IN_FILE_MANAGER

Allows applications to read audio recording files from file manager directories.

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Supported Devices:** Phone | PC/2in1 | Tablet

**Initial Version:** 20

## ohos.permission.WRITE_SOUND_RECORD_IN_FILE_MANAGER

Allows applications to write audio recording files to file manager directories.

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Supported Devices:** Phone | PC/2in1 | Tablet

**Initial Version:** 20

## ohos.permission.SANDBOX_ACCESS_MANAGER

Allows applications to access sandbox directories of other applications.

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Initial Version:** 17

## ohos.permission.REQUEST_DISABLE_NOTIFICATION

Allows background upload/download tasks of applications to be hidden from the notification bar.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Supported Devices:** General

**Initial Version:** 20

## ohos.permission.RESTORE_APP

Allows system applications to launch recovery dialogs for app restoration.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Supported Devices:** Phone | PC/2in1 | Tablet

**Initial Version:** 20

## ohos.permission.ALLOW_IOURING

Allows system applications to call io_uring-related system calls for asynchronous I/O operations.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Supported Devices:** General

**Initial Version:** 20

## ohos.permission.NFC_NOTIFICATION

Allows applications to publish NFC notification-related public events.

**Permission Level:** system_basic

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Supported Devices:** Phone

**Initial Version:** 20

## ohos.permission.kernel.ALLOW_APP_CODE_DECRYPT

Allows system applications or services to call kernel interfaces for code decryption.

With this permission, applications or services can access kernel interfaces across processes to request decryption of encrypted code content, preventing unauthorized access and further protecting application code assets.

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Supported Devices:** General

**Initial Version:** 20

## ohos.permission.GRANT_URI_PERMISSION_AS_CALLER

Allows applications to grant URI access permissions to target applications using the caller's identity.

**Permission Level:** system_core

**Authorization Mode:** system_grant

**ACL Enabled:** true

**Supported Devices:** General

**Initial Version:** 20