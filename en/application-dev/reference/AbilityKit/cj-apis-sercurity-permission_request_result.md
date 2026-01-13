# ohos.security.permission_request_result (PermissionRequestResult)

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

The permission request result object, returned when calling [requestPermissionsFromUser](cj-apis-ability_access_ctrl.md#func-requestpermissionsfromuseruiabilitycontext-arraypermissions-asynccallbackpermissionrequestresult) to request permissions, indicating the outcome of this permission request.

## Import Module

```cangjie
import kit.AbilityKit.*
```

## Usage Instructions

API sample code usage instructions:

- If the sample code has a "// index.cj" comment in the first line, it means the example can be compiled and run in the "index.cj" file of the Cangjie template project.
- If the sample requires obtaining the [Context](cj-apis-app-ability-ui_ability.md#class-context) application context, it needs to be configured in the "main_ability.cj" file of the Cangjie template project.

For the above example projects and configuration templates, please refer to [Cangjie Sample Code Instructions](../cj-development-intro.md#仓颉示例代码说明).

## class PermissionRequestResult

```cangjie
public class PermissionRequestResult {
    public var permissions: Array<String>
    public var authResults: Array<Int32>
    public var dialogShownResults = Array<Bool>()
}
```

**Function:** Constructs a permission request result object.

**System Capability:** SystemCapability.Security.AccessToken

**Initial Version:** 22

### var authResults

```cangjie
public var authResults: Array<Int32>
```

**Function:** Results of the corresponding requested permissions. -1: Not authorized. 0: Authorized. 2: Not authorized, indicating the request is invalid. Possible reasons include: target permission not declared in the configuration file; illegal permission name; some permissions have special application conditions that were not met when requesting the corresponding permission.

**Type:** Array<\Int32>

**Read/Write Capability:** Readable and Writable

**System Capability:** SystemCapability.Security.AccessToken

**Initial Version:** 22

### var dialogShownResults

```cangjie
public var dialogShownResults = Array<Bool>()
```

**Function:** Whether there was a pop-up for this permission request: true: Pop-up shown. false: No pop-up.

**Type:** Array<\Bool>

**Read/Write Capability:** Readable and Writable

**System Capability:** SystemCapability.Security.AccessToken

**Initial Version:** 22

### var permissions

```cangjie
public var permissions: Array<String>
```

**Function:** Permissions passed by the user.

**Type:** Array<\String>

**Read/Write Capability:** Readable and Writable

**System Capability:** SystemCapability.Security.AccessToken

**Initial Version:** 22