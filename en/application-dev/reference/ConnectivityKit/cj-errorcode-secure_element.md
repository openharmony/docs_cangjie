# SE (Secure Element) Error Codes

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

> **Note:**
>
> The following describes only the error codes specific to this module. For general error codes, please refer to the [Universal Error Code Documentation](../cj-errorcode-universal.md).

## 3300101 SE Service State Exception

**Error Message**

IllegalStateError, an attempt is made to use an SE session that has been closed.

**Error Description**

SE service state is abnormal.

**Possible Causes**

The SE service connection has been terminated.

**Resolution Steps**

1. Close the SE service.
2. Re-establish the connection with the SE service.

## 3300102 No Such SE Exception

**Error Message**

NoSuchElementError, the AID on the SE is not available or cannot be selected.

**Error Description**

No such SE exception.

**Possible Causes**

1. Communication exception when establishing connection with the SE service.
2. SE chip communication exception.

**Resolution Steps**

1. Close the SE service and re-establish the connection.
2. Try restarting the device.

## 3300103 Failed to Obtain Access Control Rules Exception

**Error Message**

SecurityError, the calling application cannot be granted access to this AID or the default applet on this session.

**Error Description**

Failed to obtain access control rules exception.

**Possible Causes**

1. The security element lacks the access rules required by the application.

**Resolution Steps**

1. Write the correct access rules to the security element.
2. Close the SE service and re-establish the connection.

## 3300104 SE Chip I/O Exception

**Error Message**

IOError, there is a communication problem to the reader or the SE.

**Error Description**

SE chip I/O exception.

**Possible Causes**

1. Communication exception with the SE chip.
2. SE chip state is abnormal.

**Resolution Steps**

1. Close the SE service and re-establish the connection.
2. Try restarting the device.