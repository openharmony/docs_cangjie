# Development Guide for Requesting Location Permissions

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

## Scenario Overview

Before using the [Location Kit](../reference/LocationKit/cj-apis-geo_location_manager.md) system capabilities, an application needs to verify whether it has obtained user authorization to access device location information. If authorization has not been granted, the application can request the required location permissions from the user.

The system provides the following location permissions:

- `ohos.permission.LOCATION`: Used to obtain precise location with meter-level accuracy.

- `ohos.permission.APPROXIMATELY_LOCATION`: Used to obtain approximate location with an accuracy of 5 kilometers.

For permission requirements of Location Kit interfaces, refer to: [Location Kit](../reference/LocationKit/cj-apis-geo_location_manager.md).

## Development Steps

1. Developers can declare the required permissions in the application configuration file and request user authorization. For details, refer to [Requesting User Authorization](../security/AccessToken/cj-request-user-authorization.md#向用户申请授权).

2. When the app is running in the foreground and accessing device location information, the methods for requesting location permissions are as follows:

   | Method for Requesting Location Permissions | Allowed to Request | Accuracy of Obtained Location After Successful Request |
   | -------- | -------- | -------- |
   | Request `ohos.permission.APPROXIMATELY_LOCATION` | Yes | Obtains approximate location with an accuracy of 5 kilometers. |
   | Request both `ohos.permission.APPROXIMATELY_LOCATION` and `ohos.permission.LOCATION` | Yes | Obtains precise location with meter-level accuracy. |