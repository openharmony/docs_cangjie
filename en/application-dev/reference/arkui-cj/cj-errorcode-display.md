# Screen Error Codes

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

> **Note:**
>
> This document only introduces error codes specific to this module. For general error codes, please refer to the [Universal Error Code Documentation](../cj-errorcode-universal.md).

## 1400001 Invalid Display Device

**Error Message**

Invalid display or screen.

**Error Description**

This error code is reported when attempting to operate on an invalid display device (including virtual screens).

**Possible Causes**

1. The virtual screen has not been created.

2. The virtual screen has been destroyed.

**Resolution Steps**

1. Before operating on a virtual screen, verify its existence and ensure it has been created.

2. Before operating on a virtual screen, check whether it has been destroyed. Ensure it remains active before performing any operations.

## 1400002 Unauthorized Operation

**Error Message**

Unauthorized operation.

**Error Description**

This error code is reported when attempting to perform operations on objects without proper permissions.

**Possible Causes**

Attempting to operate on virtual screen objects belonging to other processes.

**Resolution Steps**

Check for any unauthorized operations on objects from other processes and remove such illegal operations.

## 1400003 System Service Malfunction

**Error Message**

This display manager service works abnormally.

**Error Description**

This error code is reported when the system service is functioning abnormally.

**Possible Causes**

1. The screen management service failed to start properly.

2. Abnormalities in the underlying graphics composition and rendering.

**Resolution Steps**

The system service is experiencing internal malfunctions. Please retry after some time or attempt restarting the device.