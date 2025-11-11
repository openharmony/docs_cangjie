# Access Control Error Codes

> **Note:**
>
> The following describes only the error codes specific to this module. For general error codes, please refer to the [Universal Error Code Documentation](../cj-errorcode-universal.md).

## 12100001 Invalid Parameter

**Error Message**

Parameter invalid, message is ${messageInfo}.

**Possible Causes**

This error code indicates parameter validation failure. Possible causes include:

1. The tokenId value is 0.
2. The specified permission name is empty or exceeds 256 characters in length.
3. The flag value for requesting authorization/revocation is invalid.
4. Parameter check failed for listener registration.

**Resolution**

Verify input parameters and correct them to valid values.

## 12100002 tokenId Does Not Exist

**Error Message**

TokenId does not exist.

**Possible Causes**

1. The specified tokenId does not exist.
2. The process corresponding to the specified tokenId is not an application process.

**Resolution**

Verify input parameters and correct them to valid values.

## 12100003 Permission Does Not Exist

**Error Message**

Permission does not exist.

**Possible Causes**

1. The specified permissionName does not exist.
2. In authorization/revocation scenarios, the specified application tokenId has not requested the specified permissionName.
3. In permission usage record scenarios, the specified permissionName is not a user-authorized sensitive permission.

**Resolution**

Verify input parameters and correct them to valid values. [Permission List](../../security/AccessToken/cj-app-permissions.md#application-permission-list).

## 12100004 Interfaces Not Used in Pairs

**Error Message**

The interface is not used together.

**Possible Causes**

This error code indicates listener interfaces were not used in pairs. Possible causes include:

1. The current interface was called repeatedly without being used in pairs.
2. The current interface was called individually without being used in pairs.

**Resolution**

1. Verify whether the current interface requires paired usage. For example, after calling the start recording interface, the same parameters cannot be used to call the start recording interface again before calling the stop recording interface.
2. Verify whether the current interface requires paired usage. For example, the stop recording interface must be called after the start recording interface, and the unregister listener interface must be called after the register listener interface.

## 12100005 Listener Limit Exceeded

**Error Message**

The number of listeners exceeds the limit.

**Possible Causes**

This error code indicates the current number of listeners has exceeded the limit of 200.

**Resolution**

Release unused registered listeners promptly.

## 12100006 Specified Application Does Not Support Permission Grant/Revocation

**Error Message**

The specified application does not support the permissions granted or ungranted as specified.

**Possible Causes**

1. The input tokenId is the identity of a remote device, which does not yet support distributed authorization and revocation.
2. The specified tokenId corresponds to a sandbox application that is prohibited from requesting the specified permission.

**Resolution**

1. Verify whether the tokenId was obtained correctly.
2. Confirm whether the sandbox application to be authorized is a special restricted sandbox application process. Sandbox applications in certain modes are prohibited from being granted most permissions.

## 12100007 System Service Exception

**Error Message**

Service is abnormal.

**Possible Causes**

This error code indicates abnormal system service operation:

1. The permission management service failed to start normally.
2. IPC data read/write failed.

**Resolution**

The system service encountered an internal exception. Please retry later or restart the device.

## 12100008 Memory Allocation Failure

**Error Message**

Out of memory.

**Possible Causes**

Insufficient system memory.

**Resolution**

The system has insufficient memory. Please retry later or restart the device.

## 12100009 Internal Service Error

**Error Message**

Common inner error.

**Possible Causes**

Internal system service error.

**Resolution**

An internal logic error occurred. Further analysis with fault logs is required.

## 12100010 Pending Request Exists

**Error Message**

The request already exists.

**Possible Causes**

The previous request has not been processed.

**Resolution**

Please complete processing of the previous request.

## 12100011 All Permissions Already Granted

**Error Message**

All permissions in the permission list have been granted.

**Possible Causes**

All permissions have already been granted.

**Resolution**

No action needed. This error code indicates the requested permissions are already granted, and no permission setting dialog will be displayed.

## 12100012 Permission List Contains Non-Revoked Permissions

**Error Message**

The permission list contains the permission that has not been revoked by the user.

**Possible Causes**

Contains permissions not previously denied by the user.

**Resolution**

First call requestPermissionsFromUser to request permissions from the user.

## 12100013 Global Switch Already Enabled

**Error Message**

The specific global switch is already open.

**Possible Causes**

The global switch is already enabled.

**Resolution**

No action needed. This error code indicates the global switch is already enabled, and no global switch setting dialog will be displayed.