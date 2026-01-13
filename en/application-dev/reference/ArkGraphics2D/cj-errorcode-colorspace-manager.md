# Color Management Error Codes

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

> **Note:**
>
> The following describes only the error codes specific to this module. For general error codes, please refer to the [Universal Error Code Documentation](../cj-errorcode-universal.md).

## 18600001 Abnormal Parameter Value

**Error Message**

Parameter value is abnormal.

**Error Description**

This error code occurs when the parameter value does not meet the interface invocation requirements.

**Possible Causes**

The error may be reported when the parameter value exceeds the invocation range of the interface, such as when an enumeration value exceeds the defined range.

**Resolution Steps**

Before defining interface parameters, ensure that the parameter values comply with the interface parameter requirements.