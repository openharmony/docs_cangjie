# Syscap (System Capability)

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

System Capability (SystemCapability, abbreviated as SysCap) refers to each relatively independent feature in an operating system. Different devices correspond to different sets of system capabilities, where each system capability corresponds to one or more APIs. Developers can determine whether an interface is available based on system capabilities.

## func canIUse(String)

```cangjie
public func canIUse(syscap: String): Bool
```

**Function:** Queries whether the system possesses a specific system capability.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Initial Version:** 22

**Parameters:**

| Parameter Name | Type   | Required | Default Value | Description                          |
|:---------------|:-------|:---------|:--------------|:-------------------------------------|
| syscap         | String | Yes      | -             | The name of the system capability to be queried. |

**Return Value:**

| Type | Description                                                                 |
|:-----|:----------------------------------------------------------------------------|
| Bool | The query result of the system capability. `true` indicates the system possesses the capability, `false` indicates it does not. |