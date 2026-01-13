# Camera Error Codes

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

> **NOTE:**
>
> The following describes only error codes specific to this module. For general error codes, please refer to the [Universal Error Code Documentation](../cj-errorcode-universal.md).

## 7400101 Invalid Parameter

**Error Message**

Parameter missing or parameter type incorrect.

**Error Description**

Invalid parameters were passed when calling the interface.

**Possible Causes**

Invalid parameters, such as values outside the valid range or not using specified enumeration values.

**Solution**

Refer to the interface documentation and provide correct input parameters.

## 7400102 Illegal Operation

**Error Message**

Operation not allowed.

**Error Description**

Operation was not performed according to the established procedure.

**Possible Causes**

Incorrect interface execution sequence, such as performing `commitConfig` before `beginConfig`.

**Solution**

Follow the correct steps as specified in the interface documentation and guidelines.

## 7400103 Session Not Configured

**Error Message**

Session not config.

**Error Description**

An operation requiring session configuration was performed before the session was configured.

**Possible Causes**

Calling `start` operation before configuring the session.

**Solution**

Configure the session first.

## 7400104 Session Not Running

**Error Message**

Session not running.

**Error Description**

An operation requiring session running was performed before the session was running.

**Possible Causes**

Calling `capture` operation before starting the session.

**Solution**

Start the session first.

## 7400105 Session Configuration Locked

**Error Message**

Session config locked.

**Error Description**

Session configuration is locked.

**Possible Causes**

Another thread has locked the session configuration.

**Solution**

Wait for the session configuration lock to be released.

## 7400106 Device Setting Locked

**Error Message**

Device setting locked.

**Error Description**

Device configuration is locked.

**Possible Causes**

Another thread has locked the device configuration.

**Solution**

Wait for the device configuration lock to be released.

## 7400107 Camera Conflict

**Error Message**

Can not use camera cause of conflict.

**Error Description**

Unable to use the camera due to conflicts.

**Possible Causes**

Conflict between an already opened camera and the camera to be used locally.

**Solution**

Wait for the conflicting camera to be released.

## 7400108 Camera Disabled by Security Policy

**Error Message**

Camera disabled cause of security reason.

**Error Description**

Unable to use the camera due to security policies.

**Possible Causes**

Opening the camera when the application is in the background.

**Solution**

Open the camera after the application returns to the foreground.

## 7400109 Camera Device Preempted

**Error Message**

Can not use camera cause of preempted.

**Error Description**

Unable to use the camera because it has been preempted.

**Possible Causes**

Two applications simultaneously opening the same camera, causing the later application to fail.

**Solution**

N/A

## 7400110 Configuration Conflict

**Error Message**

Unresolved conflicts with current configurations.

**Error Description**

Incompatibility between the submitted configuration and the device-supported configuration.

**Possible Causes**

Setting a preview stream frame rate that exceeds the device-supported range.

**Solution**

Verify that the submitted configuration complies with the device-supported specifications.

## 7400201 Camera Service Error

**Error Message**

Camera service fatal error.

**Error Description**

Camera service exception.

**Possible Causes**

Camera service anomalies, such as service restart or cross-process call failures.

**Solution**

This is a system-level generic error with unclear occurrence scenarios. It is recommended to recreate the service.