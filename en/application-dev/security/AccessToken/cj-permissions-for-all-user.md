# Open Permissions (User Authorization)

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

All permissions listed here are user-granted (user_grant) open permissions, available to all applications.

For this type of permission, applications must not only declare the permission in the installation package but also request user authorization dynamically during runtime by displaying a pop-up dialog. Only after the user manually grants permission will the application truly obtain the corresponding permission, enabling successful access to the target operation.

<!--Del-->
> **Note:**
>
> Permissions with a level of "normal" do not involve ACL enablement fields.
<!--DelEnd-->

## Application Method

The authorization method for the following permissions is [user_grant (User Authorization)](./cj-app-permission-mgmt-overview.md#user_grant用户授权). For the application process, refer to [Declaring Permissions](./cj-declare-permissions.md) > [Requesting User Authorization](./cj-request-user-authorization.md).

## Permission List

### ohos.permission.ACCESS_BLUETOOTH

Allows an application to access Bluetooth and use Bluetooth capabilities, such as pairing and connecting to peripheral devices.

**Permission Level:** normal

**Authorization Method:** user_grant

**Initial Version:** 12

### ohos.permission.MEDIA_LOCATION

Allows an application to access geographical location information in user media files.

**Permission Level:** normal

**Authorization Method:** user_grant

**Initial Version:** 12

### ohos.permission.APP_TRACKING_CONSENT

Allows an application to read open anonymous device identifiers.

<!--RP3--><!--RP3End-->

**Permission Level:** normal

**Authorization Method:** user_grant

**Initial Version:** 12

### ohos.permission.ACTIVITY_MOTION

Allows an application to read the user's motion state.

**Permission Level:** normal

**Authorization Method:** user_grant

**Initial Version:** 12

### ohos.permission.CAMERA

Allows an application to use the camera.

**Permission Level:** normal

**Authorization Method:** user_grant

**Initial Version:** 12

### ohos.permission.DISTRIBUTED_DATASYNC

Allows data exchange between different devices.

**Permission Level:** normal

**Authorization Method:** user_grant

**Initial Version:** 12

### ohos.permission.LOCATION_IN_BACKGROUND

Allows an application to obtain device location information while running in the background.

Due to security and privacy requirements, applications cannot request background location permission via pop-up dialogs. If an application requires background location permission, it must guide users to manually grant the permission in the settings interface.

**Application Process:**

1. Declare the permission in the "module.json5" configuration file [Declaring Permissions](./cj-declare-permissions.md).

    Since foreground location permission must be requested before applying for background location permission, developers should configure both the background location permission (ohos.permission.LOCATION_IN_BACKGROUND) and foreground location permission. There are two scenarios for foreground location permission:
    - Request foreground approximate location permission: [ohos.permission.APPROXIMATELY_LOCATION](#ohospermissionapproximately_location).
    - Request foreground precise location permission: [ohos.permission.APPROXIMATELY_LOCATION](#ohospermissionapproximately_location) and [ohos.permission.LOCATION](#ohospermissionlocation).
2. The application must request the corresponding foreground location permission from the user via a pop-up dialog.
3. After the user grants the foreground location permission via the pop-up, the application should inform the user to grant background location permission in the settings interface through pop-ups or prompts.
4. The user selects "Always Allow" in the settings interface to manually grant the permission for accessing location information.

    Settings Path:
    <!--RP1-->
   - Path 1: Settings > Privacy > Permission Management > Location > *Specific Application*
   - Path 2: Settings > Privacy > Permission Management > Applications > *Specific Application* > Location
   <!--RP1End-->

**Permission Level:** normal

**Authorization Method:** user_grant

**Initial Version:** 12

### ohos.permission.LOCATION

Allows an application to obtain device location information.

**Prerequisite:** Must be requested together with the approximate location permission [ohos.permission.APPROXIMATELY_LOCATION](#ohospermissionapproximately_location).

**Permission Level:** normal

**Authorization Method:** user_grant

**Initial Version:** 12

### ohos.permission.APPROXIMATELY_LOCATION

Allows an application to obtain approximate device location information.

**Permission Level:** normal

**Authorization Method:** user_grant

**Initial Version:** 12

### ohos.permission.MICROPHONE

Allows an application to use the microphone.

**Permission Level:** normal

**Authorization Method:** user_grant

**Initial Version:** 12

### ohos.permission.READ_CALENDAR

Allows an application to read calendar information.

**Permission Level:** normal

**Authorization Method:** user_grant

**Initial Version:** 12

### ohos.permission.WRITE_CALENDAR

Allows an application to add, remove, or modify calendar events.

**Permission Level:** normal

**Authorization Method:** user_grant

**Initial Version:** 12

### ohos.permission.READ_HEALTH_DATA

Allows an application to read user health data.

**Permission Level:** normal

**Authorization Method:** user_grant

**Initial Version:** 12

### ohos.permission.ACCESS_NEARLINK

Allows an application to access NearLink and use NearLink capabilities, such as pairing and connecting to peripheral devices.

**Permission Level:** normal

**Authorization Method:** user_grant

**Initial Version:** 12

### ohos.permission.READ_WRITE_DOWNLOAD_DIRECTORY

Allows an application to access the Download directory and its subdirectories in the public directory.

<!--RP2--><!--RP2End-->

**Permission Level:** normal

**Authorization Method:** user_grant

**Supported Devices:** PC/2in1 | Tablet

**Initial Version:** 12

### ohos.permission.READ_WRITE_DOCUMENTS_DIRECTORY

Allows an application to access the Documents directory and its subdirectories in the public directory.

<!--RP2--><!--RP2End-->

**Permission Level:** normal

**Authorization Method:** user_grant

**Supported Devices:** PC/2in1 | Tablet

**Initial Version:** 12

## ohos.permission.CUSTOM_SCREEN_CAPTURE

Allows an application to capture screen images.

After obtaining this permission, the application can perform operations such as screenshots.

**Permission Level:** system_basic

**Authorization Method:** user_grant

**Supported Devices:** PC/2in1 | Tablet

**Initial Version:** 12