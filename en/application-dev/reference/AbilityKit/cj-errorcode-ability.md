# Meta Capability Subsystem Error Codes

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

> **Note:**
>
> The following only introduces error codes specific to this module. For general error codes, please refer to the [Universal Error Code Documentation](../cj-errorcode-universal.md).

## 16000001 Specified Ability Does Not Exist

**Error Message**

The specified ability does not exist.

**Error Description**

This error code is returned when the specified ability name does not exist.

**Possible Causes**

The queried ability does not exist.

**Resolution Steps**

1. Verify that the bundleName, moduleName, and abilityName in the want are correct.
2. Check whether the application corresponding to the bundleName in the want is installed. Use the following command to query the list of installed applications. If the bundleName is not in the query results, the application is not installed successfully.

    ``` text
    hdc shell bm dump -a
    ```

3. For multi-HAP applications, confirm whether the HAP to which the ability belongs has been installed. Use the following command to query the package information of the application. If the corresponding HAP and ability are not found in the installed application, the HAP to which the ability belongs has not been installed.

    ``` text
    hdc shell bm dump -n package_name
    ```

## 16000002 Incorrect Ability Type

**Error Message**

Incorrect ability type.

**Error Description**

This error code is returned when the ability type called by the interface is incorrect.

**Possible Causes**

The ability type where the interface is called does not support this interface call.

**Resolution Steps**

1. Verify that the bundleName, moduleName, and abilityName in the want are correct.
2. Call different interfaces based on the ability type.

## 16000003 Specified ID Does Not Exist

**Error Message**

The specified ID does not exist.

**Error Description**

This error code is returned when the specified ID does not exist.

**Possible Causes**

The target ID for the operation does not exist.

**Resolution Steps**

Confirm whether the ID for the operation exists.

## 16000004 Visibility Verification Failed

**Error Message**

Failed to start the invisible ability.

**Error Description**

This error code is returned when visibility verification fails.

**Possible Causes**

Application visibility verification failed.

**Resolution Steps**

1. In the Stage model, if exception 16000004 is thrown when launching an application, it indicates that the called application failed. Check whether the exported configuration in the Ability field of the module.json5 of the called application is set to true. If this field is true, the ability can be called by other applications; if false, it cannot.
2. If an application needs to launch an ability with exported set to false, apply for the ohos.permission.START_INVISIBLE_ABILITY permission (this permission can only be applied for by system applications).

## 16000005 Specified Process Permission Verification Failed

**Error Message**

The specified process does not have the permission.

**Error Description**

This error code is returned when the specified process permission verification fails.

**Possible Causes**

The specified process permission verification failed.

**Resolution Steps**

Confirm whether the permissions of the specified process are correct.

## 16000006 Cross-User Operations Are Not Allowed

**Error Message**

Cross-user operations are not allowed.

**Error Description**

This error code is returned when an application performs cross-user operations.

**Possible Causes**

The application performed cross-user operations.

**Resolution Steps**

Confirm whether cross-user operations were performed.

## 16000007 Service Busy

**Error Message**

Service busy. There are concurrent tasks. Try again later.

**Error Description**

This error code is returned when the service is busy.

**Possible Causes**

The service is busy.

**Resolution Steps**

The service is busy. Please try again later.

## 16000008 Crowdtesting Application Expired

**Error Message**

The crowdtesting application expires.

**Error Description**

This error code is returned when a crowdtesting application expires.

**Possible Causes**

The crowdtesting application has expired and cannot be opened.

**Resolution Steps**

Check whether the crowdtesting application has expired. Expired crowdtesting applications cannot be launched.

## 16000009 Wukong Mode: Starting/Stopping Ability Not Allowed

**Error Message**

An ability cannot be started or stopped in Wukong mode.

**Error Description**

This error code is returned when starting or stopping an ability in Wukong mode.

**Possible Causes**

Starting or stopping an ability is not allowed in Wukong mode.

**Resolution Steps**

Exit Wukong mode before attempting to start or stop the ability. Do not start or stop abilities in Wukong mode.

## 16000010 Continuation Flag Not Allowed

**Error Message**

The call with the continuation flag is forbidden.

**Error Description**

This error code is returned when a call carries the continuation flag.

**Possible Causes**

The current call does not allow the continuation flag.

**Resolution Steps**

Check whether the continuation flag is included.

## 16000011 Context Object Does Not Exist

**Error Message**

The context does not exist.

**Error Description**

This error code is returned when the context object does not exist.

**Possible Causes**

The current context object does not exist.

**Resolution Steps**

Check whether the context object is available.

## 16000012 Application Controlled

**Error Message**

The application is controlled.

**Error Description**

This error code is returned when an application is controlled by the application market.

**Possible Causes**

The application is suspected of malicious behavior and is controlled by the application market, preventing it from being launched.

**Resolution Steps**

It is recommended to uninstall the application.

## 16000013 Application Controlled by EDM

**Error Message**

The application is controlled by EDM.

**Error Description**

This error code is returned when an application is controlled by Enterprise Device Manager (EDM).

**Possible Causes**

The application is controlled by enterprise device management.

**Resolution Steps**

Contact the relevant personnel of enterprise device management.

## 16000015 Service Timeout

**Error Message**

Service timeout.

**Error Description**

This error code is returned when the service times out.

**Possible Causes**

The service timed out.

**Resolution Steps**

The service timed out. Please try again later.

## 16000017 Previous Ability Not Started: Queued for Later Launch

**Error Message**

Another ability is being started. Wait until it finishes starting.

**Error Description**

Too many abilities need to be started. Due to limited system processing capacity, requests are queued and processed in order.

**Possible Causes**

High system concurrency.

**Resolution Steps**

No action is required. Wait for the launch to complete.

## 16000018 Third-Party Application Redirection Restricted for API Version 11+

**Error Message**

Redirection to a third-party application is not allowed in API version 11 or later.

**Error Description**

When the application API version is greater than 11, explicit redirection to other third-party applications is not allowed.

**Resolution Steps**

Use implicit launch or openLink to redirect to other applications.

## 16000019 No Matching Ability Found for Implicit Launch

**Error Message**

No matching ability is found.

**Error Description**

No matching ability is found for implicit launch.

**Resolution Steps**

Modify the matching criteria for implicit launch.

## 16000050 Internal Error

**Error Message**

Internal error.

**Error Description**

This error code is returned when internal processing errors occur, such as memory allocation or multi-threading exceptions.

**Possible Causes**

General kernel errors, including but not limited to: internal objects being null, processing timeouts, failure to obtain application information from package management, failure to obtain system services, reaching the upper limit of ability instances, etc.

**Resolution Steps**

1. Check whether the system has sufficient memory and whether the system version in use is abnormal.
2. Check whether too many abilities have been launched.
3. Try restarting the device.

## 16000051 Network Error

**Error Message**

Network error.

**Error Description**

This error code is returned when a network error occurs.

**Possible Causes**

The network is unavailable.

**Resolution Steps**

A network error occurred. Please try again later or reconnect to the network.

## 16000052 Installation-Free Not Supported

**Error Message**

Installation-free is not supported.

**Error Description**

This error code is returned when the current application does not support installation-free.

**Possible Causes**

The application package does not meet the installation-free requirements, such as exceeding the size limit.

**Resolution Steps**

Check whether the application supports installation-free.

## 16000053 Ability Not on Top of UI

**Error Message**

The ability is not on the top of the UI.

**Error Description**

This error code is returned when the current application is not displayed at the top of the UI.

**Possible Causes**

For installation-free launch, the application must be in the foreground, but it is not displayed at the top of the UI.

**Resolution Steps**

Check whether the current application is displayed at the top of the UI.

## 16000054 Installation-Free Service Busy

**Error Message**

The installation-free service is busy. Try again later.

**Error Description**

This error code is returned when the installation-free service is busy.

**Possible Causes**

A download or installation task for the same atomic service is already in progress.

**Resolution Steps**

The installation-free service is busy. Please try again later.## 16000055 Installation-Free Timeout

**Error Message**

Installation-free timed out.

**Error Description**

This error code is returned when the installation-free operation times out.

**Possible Causes**

Installation-free operation timed out.

**Resolution Steps**

Wait and retry the installation-free operation later.

## 16000056 Installation-Free Not Allowed for Other Applications

**Error Message**

Installation-free is not allowed for other applications.

**Error Description**

This error code is returned when attempting to perform installation-free for other applications.

**Possible Causes**

Installation-free is not permitted for other applications.

**Resolution Steps**

Verify that the correct application is selected for installation-free.

## 16000057 Cross-Device Installation-Free Not Supported

**Error Message**

Cross-device installation-free is not supported.

**Error Description**

This error code is returned when cross-device installation-free is not supported.

**Possible Causes**

Cross-device installation-free is not supported.

**Resolution Steps**

Ensure the application is not being installed across devices.

## 16000058 Invalid URI Flag Specified

**Error Message**

Invalid URI flag.

**Error Description**

The specified URI flag is invalid.

**Possible Causes**

Incorrect parameters were passed.

**Resolution Steps**

Verify that the passed parameters belong to the Uri flag.

## 16000059 Invalid URI Type Specified

**Error Message**

Invalid URI type.

**Error Description**

The specified URI type is invalid.

**Possible Causes**

Incorrect parameters were passed. Currently, URI authorization management only supports file-type URIs.

**Resolution Steps**

Ensure the passed parameters belong to supported URI types.

## 16000060 Sandbox Application Cannot Grant URI Permission

**Error Message**

A sandbox application cannot grant URI permission.

**Error Description**

This error code is returned when a sandbox application attempts to grant URI permission.

**Possible Causes**

Sandbox applications are not allowed to grant URI permissions.

**Resolution Steps**

Ensure the application is not a sandbox application.

## 16000061 Operation Not Supported

**Error Message**

Operation not supported.

**Error Description**

This error code is returned when the operation is not supported on the current system.

**Possible Causes**

The operation is not supported on the current system.

**Resolution Steps**

Verify whether the operation is supported on the current system.

## 16000062 Number of Child Processes Exceeds Limit

**Error Message**

The number of child processes exceeds the upper limit.

**Error Description**

This error code is returned when the number of child processes created has reached the upper limit during a child process creation request.

**Possible Causes**

The maximum number of child processes has been reached.

**Resolution Steps**

Check if the number of child processes has reached the limit. The upper limit for child processes is 512.

## 16000063 Invalid Target Component for Application Restart

**Error Message**

The target to restart does not belong to the current application or is not a UIAbility.

**Error Description**

This error code is returned when the specified component name or type is invalid during application restart.

**Possible Causes**

The specified component name or type is invalid.

**Resolution Steps**

Ensure the specified component belongs to the current application and is of type UIAbility.

## 16000064 Application Restart Too Frequent

**Error Message**

Restart too frequently. Try again at least 10s later.

**Error Description**

This error code is returned when attempting to restart an application and launch a specified component within 10 seconds of a previous call.

**Possible Causes**

The interface was called too frequently.

**Resolution Steps**

Wait at least 10 seconds before calling the interface again.

## 16000065 API Call Requires Ability in Foreground

**Error Message**

The API can be called only when the ability is running in the foreground.

**Error Description**

This error code is returned when the ability is not in the foreground.

**Possible Causes**

The ability was not in the foreground when the interface was called.

**Resolution Steps**

Bring the ability to the foreground before calling the interface.

## 16000066 Wukong Mode Restricts Ability Movement

**Error Message**

An ability cannot switch to the foreground or background in Wukong mode.

**Error Description**

This error code is returned when attempting to move an ability to the foreground or background in Wukong mode.

**Possible Causes**

Wukong mode does not allow moving abilities to the foreground or background.

**Resolution Steps**

Exit Wukong mode before attempting to move the ability. Do not move abilities to the foreground or background in Wukong mode.

## 16000067 StartOptions Parameter Validation Failed

**Error Message**

The StartOptions check failed.

**Error Description**

This error code is returned when StartOptions-related parameter validation fails.

**Possible Causes**

1. When calling startAbility, if processMode is set to NEW_PROCESS_ATTACH_TO_STATUS_BAR_ITEM or ATTACH_TO_STATUS_BAR_ITEM but the application has no icon in the status bar, this error code is returned.
2. When calling showAbility/hideAbility, if the caller was not started in NEW_PROCESS_ATTACH_TO_STATUS_BAR_ITEM or ATTACH_TO_STATUS_BAR_ITEM mode, this error code is returned.

**Resolution Steps**

Verify the StartOptions parameter configuration and ensure all constraints are met.

## 16000068 Ability Already Running

**Error Message**

The ability is already running.

**Error Description**

This error code is returned when the target ability is already running.

**Possible Causes**

When calling startAbility, if processMode and startupVisibility are specified, and the target ability's launchType is singleton or specified while the ability is already running, this error code is returned.

**Resolution Steps**

If the target ability's launchType is singleton or specified, avoid repeatedly calling startAbility with processMode and startupVisibility.

## 16000069 Strict Mode Restricts Third-Party App Launch

**Error Message**

The extension cannot start the third party application.

**Error Description**

In strict mode, this type of extension is not allowed to launch third-party applications.

**Possible Causes**

The current extension is in strict mode, and the extension type does not permit launching third-party applications in strict mode.

**Resolution Steps**

1. Check the strict mode conditions for the extension type.
2. Launch the extension in non-strict mode.

## 16000070 Strict Mode Restricts ServiceExtensionAbility Launch

**Error Message**

The extension cannot start the service.

**Error Description**

In strict mode, this type of extension is not allowed to launch specified ServiceExtensionAbility.

**Possible Causes**

The current extension is in strict mode, and the extension type does not permit launching specified ServiceExtensionAbility in strict mode.

**Resolution Steps**

1. Check the strict mode conditions for the extension type.
2. Launch the extension in non-strict mode.

## 16000071 App Clone Not Supported

**Error Message**

App clone is not supported.

**Error Description**

This error code is returned when the application does not support clone mode.

**Possible Causes**

This error code is returned when calling getCurrentAppCloneIndex in an application that does not support cloning.

**Resolution Steps**

Avoid calling getCurrentAppCloneIndex in applications that do not support cloning.

<!--Del-->
## 16000072 App Multi-Instance Not Supported

**Error Message**

App clone or multi-instance is not supported.

**Error Description**

This error code is returned when the application does not support multi-instance mode.

**Possible Causes**

This error code is returned when calling getRunningMultiAppInfo to query multi-instance information for an application that does not support multi-instance.

**Resolution Steps**

Ensure the application supports multi-instance before calling getCurrentAppCloneIndex.
<!--DelEnd-->

## 16000073 Invalid appCloneIndex Value

**Error Message**

The app clone index is invalid.

**Error Description**

This error code is returned when an invalid appCloneIndex is passed.

**Possible Causes**

1. When calling startAbility, if the appCloneIndex carried by ohos.extra.param.key.appCloneIndex is invalid, this error code is returned.
<!--Del-->
2. When calling isAppRunning, if the input parameter appCloneIndex is invalid, this error code is returned.
<!--DelEnd-->

**Resolution Steps**

Verify that the appCloneIndex meets all constraints.

## 16000074 Caller Not Found for RequestCode

**Error Message**

The caller does not exist.

**Error Description**

This error code is returned when attempting to return results via backTocallerAbilityResult but the caller corresponding to the requestCode cannot be found.

**Possible Causes**

1. The requestCode was not obtained from the CALLER_REQUEST_CODE field in the want.
2. The caller corresponding to the requestCode has been destroyed or the result has already been returned.

**Resolution Steps**

1. Verify that the requestCode was obtained from CALLER_REQUEST_CODE in the want.
2. Check if the caller has been destroyed or the result has already been returned.

## 16000075 Back to Caller Not Supported

**Error Message**

Not support back to caller.

**Error Description**

This error code is returned when returning to the caller via backToCallerAbilityWithResult is not supported.

**Possible Causes**

The current application has not configured linkFeature or has not passed system review.

**Resolution Steps**

1. Ensure the current application has configured the linkFeature field in module.json5.
2. Verify that the declared linkFeature value is correct, matches the actual functionality of the application link, and that the application has passed system review.

## 16000076 Specified APP_INSTANCE_KEY Does Not Exist

**Error Message**

The APP_INSTANCE_KEY is invalid.

**Error Description**

This error code is returned when the specified APP_INSTANCE_KEY does not exist.

**Possible Causes**

The application instance does not contain the instance specified by APP_INSTANCE_KEY.

**Resolution Steps**

Ensure the passed APP_INSTANCE_KEY is valid.## 16000077 Maximum Number of Application Instances Reached

**Error Message**

The number of app instances reaches the limit.

**Error Description**

This error code is returned when attempting to create additional application instances after reaching the configured maximum limit.

**Possible Causes**

Failure to check whether the current instance count has reached the application's self-defined upper limit before creating new instances.

**Resolution Steps**

Adjust the configured instance limit or delete existing instances before creating new ones.

## 16000078 Multi-instance Not Supported

**Error Message**

The multi-instance is not supported.

**Error Description**

The application does not support multiple instances.

**Possible Causes**

1. The target application is not configured for multi-instance operation.
2. The current device type does not support multi-instance.

**Resolution Steps**

1. Configure multi-instance support for the target application.
2. Invoke this method on 2-in-1 devices.

## 16000079 Specifying APP_INSTANCE_KEY Not Supported

**Error Message**

The APP_INSTANCE_KEY cannot be specified.

**Error Description**

APP_INSTANCE_KEY and CREATE_APP_INSTANCE_KEY cannot be specified simultaneously. This error code is returned when both parameters are provided.

**Possible Causes**

Excessive parameter input.

**Resolution Steps**

Choose either APP_INSTANCE_KEY or CREATE_APP_INSTANCE_KEY, but not both.

## 16000080 Instance Creation Not Supported

**Error Message**

Creating an instance is not supported.

**Error Description**

Applications can only use CREATE_APP_INSTANCE_KEY to create their own instances. Cross-application instance creation during launch is prohibited, triggering this error code.

**Possible Causes**

Incorrect parameter usage scenario.

**Resolution Steps**

Remove the CREATE_APP_INSTANCE_KEY parameter.

## 16000082 UIAbility Startup Incomplete in Singleton Mode

**Error Message**

The UIAbility is being started.

**Error Description**

For UIAbilities with "singleton" launch mode, startup interfaces cannot be called again before the initial startup completes, otherwise this error code is returned.

**Possible Causes**

The UIAbility is in singleton mode and currently initializing.

**Resolution Steps**

Ensure the UIAbility completes startup before initiating new launch tasks.

## 16000100 AbilityMonitor Lifecycle Monitoring Failure

**Error Messages**

- Calling AddAbilityMonitor failed.
- Calling AddAbilityMonitorSync failed.
- Calling RemoveAbilityMonitor failed.
- Calling RemoveAbilityMonitorSync failed.
- Calling WaitAbilityMonitor failed.
- Calling GetCurrentTopAbility failed.
- Calling DoAbilityForeground failed.
- Calling DoAbilityBackground failed.
- Calling FinishTest failed.
- Calling AddAbilityStageMonitor failed.
- Calling AddAbilityStageMonitorSync failed.
- Calling RemoveAbilityStageMonitor failed.
- Calling RemoveAbilityStageMonitorSync failed.
- Calling WaitAbilityStageMonitor failed.

**Error Description**

This error code indicates failure in executing AbilityMonitor methods for monitoring specified Ability lifecycle changes.

**Possible Causes**

Failure to create AbilityDelegatorRegistry instance.

**Resolution Steps**

Verify successful creation of AbilityDelegatorRegistry instance.

## 16000101 Shell Command Execution Failure

**Error Message**

Failed to run the shell command.

**Error Description**

Returned when the command is not a valid shell command.

**Possible Causes**

Invalid shell command syntax.

**Resolution Steps**

Validate the command's shell compatibility.

## 16000151 Invalid wantAgent Object

**Error Message**

Invalid wantAgent object.

**Error Description**

Returned when an invalid wantAgent object is passed to the interface.

**Possible Causes**

Invalid wantAgent object parameter.

**Resolution Steps**

Inspect the wantAgent object passed to the interface.

## 16000152 wantAgent Object Not Found

**Error Message**

The wantAgent object does not exist.

**Error Description**

Returned when a non-existent wantAgent object is provided.

**Possible Causes**

Nonexistent wantAgent object reference.

**Resolution Steps**

Validate the wantAgent object's existence.

## 16000153 wantAgent Object Canceled

**Error Message**

The wantAgent object has been canceled.

**Error Description**

Returned when attempting to use a canceled wantAgent object.

**Possible Causes**

The referenced wantAgent trigger has been canceled.

**Resolution Steps**

Check the wantAgent object's cancellation status.

## 16100001 URI-specified Ability Not Found

**Error Message**

The ability with the specified URI does not exist.

**Error Description**

Returned when querying a non-existent Ability via URI.

**Possible Causes**

Target Ability does not exist.

**Resolution Steps**

Confirm the queried Ability's existence.

## 16100002 Incorrect Ability Type for Interface Call

**Error Message**

Incorrect ability type.

**Error Description**

Returned when an interface call targets an incompatible Ability type.

**Possible Causes**

Interface call attempted on unsupported Ability type.

**Resolution Steps**

1. Verify package name matches correct Ability.
2. Use type-specific interfaces appropriately.

## 16200001 Caller Component Released

**Error Message**

The caller has been released.

**Error Description**

Returned when attempting to use a released common component caller.

**Possible Causes**

Caller component has been garbage collected.

**Resolution Steps**

1. Re-register valid common component caller interface.
2. Verify context.startAbility's context Ability is still running.
3. For sequential startAbility/terminateSelf calls, ensure receiving startAbility callback before terminateSelf.

## 16200002 Invalid Callee Component

**Error Message**

The callee does not exist.

**Error Description**

Returned when referencing a non-existent common component callee.

**Possible Causes**

Target callee component unavailable.

**Resolution Steps**

Verify callee component existence.

## 16200003 Release Failure

**Error Message**

Release error. The caller does not call any callee.

**Error Description**

Returned during failed component release.

**Possible Causes**

Caller never registered any callee component.

**Resolution Steps**

Confirm callee component registration status.

## 16200004 Method Already Registered

**Error Message**

The method has been registered.

**Error Description**

Returned for duplicate method registration attempts.

**Possible Causes**

Method previously registered with callee component.

**Resolution Steps**

Check method registration history.

## 16200005 Method Not Registered

**Error Message**

The method has not been registered.

**Error Description**

Returned when invoking unregistered methods.

**Possible Causes**

Method not present in callee component registry.

**Resolution Steps**

Verify method registration status.

## 16200006 Resident Process Permission Denied

**Error Message**

The caller application can only set the resident status of the configured process.

**Error Description**

Returned for unauthorized resident process configuration attempts.

**Possible Causes**

Caller lacks resident process enablement permissions.

**Resolution Steps**

Query caller's resident process permissions from database during interface calls.

## 16300001 Specified Mission Not Found

**Error Message**

Mission not found.

**Error Description**

Returned when referencing non-existent missions.

**Possible Causes**

Target mission unavailable.

**Resolution Steps**

Confirm mission existence.

## 16300002 Mission Listener Not Found

**Error Message**

The specified mission listener does not exist.

**Error Description**

Returned when referencing non-existent mission listeners.

**Possible Causes**

Target listener unavailable.

**Resolution Steps**

Verify listener registration.

## 16300003 Target Application Mismatch

**Error Message**

The target application is not the current application.

**Error Description**

Returned when launching non-self applications.

**Possible Causes**

Launched application differs from caller.

**Resolution Steps**

Ensure target application matches caller identity.```markdown
## 18500001 Specified Bundle Name Invalid

**Error Message**

The bundle does not exist or no patch has been applied.

**Error Description**

This error code is returned when the specified bundle name is invalid.

**Possible Causes**

The target bundle does not exist or is not installed.

**Resolution Steps**

Verify whether the target application is installed.

## 18500002 Specified Patch Package Invalid

**Error Message**

Invalid patch package.

**Error Description**

This error code is returned when the specified patch package is invalid, non-existent, or inaccessible.

**Possible Causes**

The target patch package file does not exist or is inaccessible.

**Resolution Steps**

1. Verify the validity of the provided patch package file path.
2. Check whether you have permission to access the patch package file.

## 18500003 Patch Package Deployment Failed

**Error Message**

Failed to deploy the patch.

**Error Description**

This error code is returned when patch package deployment fails.

**Possible Causes**

1. The `type` field in `patch.json` must be either `patch` or `hotreload`; otherwise, deployment fails.
2. Deployment fails if the HAP package corresponding to `bundleName` is not installed.
3. `bundleName` and `versionCode` must match those of the installed HAP application. For `patch` type, `versionName` must also match; otherwise, deployment fails.
4. If a patch package has already been deployed, the `versionCode` of the new patch package must be greater than that of the previous one; otherwise, deployment fails.
5. For `patch`-type packages, signature verification is performed. The signing certificate must match the application's certificate; otherwise, deployment fails.
6. For debug versions deploying `patch`-type packages: if an active patch package of `hotreload` type exists, deployment fails.
7. For debug versions deploying `hotreload`-type packages: if an active patch package of `patch` type exists, deployment fails. For release versions, deployment always fails.

**Resolution Steps**

Verify whether the patch package complies with the rules.

## 18500004 Patch Package Enablement Failed

**Error Message**

Failed to enable the patch package.

**Error Description**

This error code is returned when patch package enablement fails.

**Possible Causes**

The patch package is in an incorrect state during enablement.

**Resolution Steps**

Check the patch package status.

## 18500005 Patch Package Deletion Failed

**Error Message**

Failed to remove the patch package.

**Error Description**

This error code is returned when patch package deletion fails.

**Possible Causes**

The patch package is in an incorrect state during deletion.

**Resolution Steps**

Check the patch package status.

## 18500006 Patch Loading Failed

**Error Message**

Failed to load the patch.

**Error Description**

This error code is returned when patch loading fails.

**Possible Causes**

The Ark engine failed to load the patch.

**Resolution Steps**

Verify the correctness of the patch package.

## 18500007 Old Patch Unloading Failed

**Error Message**

Failed to unload the patch.

**Error Description**

This error code is returned when the Ark engine fails to unload an old patch.

**Possible Causes**

The Ark engine failed to unload the patch.

**Resolution Steps**

Verify the correctness of the patch package.

## 18500008 Quick Fix Internal Error

**Error Message**

Internal error.

**Error Description**

This error code is returned for internal processing errors such as memory allocation or multithreading exceptions.

**Possible Causes**

Generic kernel errors related to memory allocation or multithreading.

**Resolution Steps**

Ensure sufficient system memory is available.

## 18500009 Ongoing Quick Fix Task for the Application

**Error Message**

The application has an ongoing quick fix task.

**Error Description**

This error code is returned when the application has an ongoing quick fix task.

**Possible Causes**

The target application for quick fix rollback has an ongoing quick fix task.

**Resolution Steps**

Wait for the quick fix task to complete.

## 16300004 Specified Observer Not Found

**Error Message**

observer not found.

**Error Description**

This error code is returned when the specified observer does not exist.

**Possible Causes**

The observer does not exist or has been unregistered.

**Resolution Steps**

Check for duplicate observer unregistration.

## 16300005 Specified Package Information Not Found

**Error Message**

The target bundle does not exist.

**Error Description**

This error code is returned when preloaded application package information does not exist.

**Possible Causes**

Incorrect `bundleName`, `userId`, or `appIndex` parameters prevent querying relevant package information.

**Resolution Steps**

Verify the correctness of the `bundleName`, `userId`, and `appIndex` parameters.

## 29600001 Image Editing Internal Error

**Error Message**

Internal error.

**Error Description**

This error code is returned for internal errors during image saving, such as memory allocation or multithreading exceptions.

**Possible Causes**

Generic kernel errors related to memory allocation or multithreading. Specific causes may include null internal objects or timeout issues.

**Resolution Steps**

1. Ensure sufficient system memory and check for abnormal system versions.
2. Try rebooting the device.

## 29600002 Image Input Error

**Error Message**

Image input error.

**Error Description**

This error code is returned when the image URI does not exist or the image cannot be parsed.

**Possible Causes**

The URI does not exist or points to a non-image file.

**Resolution Steps**

Verify the file's existence and ensure it is an image file.

## 29600002 Image Size Exceeds Limit

**Error Message**

Image too big.

**Error Description**

The input image size exceeds the limit.

**Possible Causes**

This error code is returned when the input image size exceeds 50MB.

**Resolution Steps**

1. Attempt to reduce the edited image size below 50MB.
2. Validate the image size.

## 16300007 Specified Atomic Service Download/Install Task Not Found

**Error Message**

The target free install task does not exist.

**Error Description**

This error code is returned when the specified atomic service download/install task does not exist during window opening.

**Possible Causes**

Incorrect `bundleName`, `moduleName`, `abilityName`, or `startTime` parameters prevent querying relevant atomic service download/install task information.

**Resolution Steps**

Verify the correctness of the `bundleName`, `moduleName`, `abilityName`, or `startTime` parameters.
```