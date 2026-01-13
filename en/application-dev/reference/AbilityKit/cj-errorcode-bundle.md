# Package Management Subsystem Common Error Codes

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

## 17700001 Specified bundleName does not exist

**Error Message**  
The specified bundle name is not found.

**Error Description**  
When calling query interfaces, the input bundleName does not exist.

**Possible Causes**  
1. Incorrect bundleName input.  
2. The corresponding application is not installed in the system.

**Resolution Steps**  
1. Verify the spelling of bundleName.  
2. Confirm whether the corresponding application is installed.

## 17700002 Specified moduleName does not exist

**Error Message**  
The specified module is not found.

**Error Description**  
When calling query or installation-free related interfaces, the input moduleName does not exist.

**Possible Causes**  
1. Incorrect moduleName input.  
2. The corresponding application does not have this module installed.

**Resolution Steps**  
1. Verify the spelling of moduleName.  
2. Confirm whether the corresponding application has this module installed.

## 17700003 Specified abilityName does not exist

**Error Message**  
The specified ability is not found.

**Error Description**  
When calling query interfaces, the input abilityName does not exist.

**Possible Causes**  
1. Incorrect abilityName input.  
2. The corresponding application does not have an ability matching this abilityName.

**Resolution Steps**  
1. Verify the spelling of abilityName.  
2. Confirm whether the corresponding application has an ability matching this abilityName.

## 17700004 Specified user does not exist

**Error Message**  
The specified user ID is not found.

**Error Description**  
When calling user-related interfaces, the input user does not exist.

**Possible Causes**  
1. Incorrect username input.  
2. The user does not exist in the system.

**Resolution Steps**  
1. Verify the spelling of the username.  
2. Confirm whether the user exists in the system.

## 17700005 Specified appId is an empty string

**Error Message**  
The specified app ID is empty string.

**Error Description**  
When calling interfaces in the appControl module, the input appId is an empty string.

**Possible Causes**  
The input appId is an empty string.

**Resolution Steps**  
Check whether appId is an empty string.

## 17700006 Queried permission does not exist

**Error Message**  
The specified permission is not found.

**Error Description**  
When calling the getPermissionDef interface in the bundleManager module, the input permission does not exist.

**Possible Causes**  
1. Incorrect permission name spelling.  
2. The corresponding permission does not exist in the system.

**Resolution Steps**  
1. Verify the spelling of the permission.  
2. Confirm whether the permission exists in the system.

## 17700007 Invalid device ID input

**Error Message**  
The specified device ID is not found.

**Error Description**  
When calling interfaces in the distributedBundle module, the input device ID is invalid.

**Possible Causes**  
1. Incorrect deviceId spelling.  
2. The deviceId does not exist.

**Resolution Steps**  
1. Verify the spelling of deviceId.  
2. Confirm whether the deviceId exists.

## 17700010 Application installation failed due to file parsing failure

**Error Message**  
Failed to install the HAP because the HAP fails to be parsed.

**Error Description**  
When calling the install interface in the installer module, the input HAP failed to be parsed.

**Possible Causes**  
1. The HAP format is not ZIP.  
2. The HAP configuration file does not comply with JSON format.  
3. The HAP configuration file lacks required fields.

**Resolution Steps**  
1. Confirm the HAP format is ZIP.  
2. Confirm the HAP configuration file complies with JSON format.  
3. Check whether DevEco Studio shows error prompts during HAP compilation - missing fields will trigger corresponding errors.

## 17700011 Application installation failed due to signature verification failure

**Error Message**  
Failed to install the HAP because the HAP signature fails to be verified.

**Error Description**  
When calling the install interface in the installer module, application installation failed due to signature verification failure.

**Possible Causes**  
1. The HAP is unsigned.  
2. The HAP signature source is unreliable.  
3. The signature of the HAP to be upgraded does not match the installed HAP.  
4. Signatures of multiple HAPs are inconsistent.

**Resolution Steps**  
1. Confirm whether the HAP is successfully signed.  
2. Confirm the HAP signature certificate is obtained from the application market.  
3. Confirm multiple HAPs use the same certificate for signing.  
4. Confirm the upgrade HAP uses the same signature certificate as the installed HAP.

## 17700012 Application installation failed due to invalid package path or oversized file

**Error Message**  
Failed to install the HAP because the HAP path is invalid or the HAP is too large.

**Error Description**  
When calling the install interface in the installer module, application installation failed due to invalid package path or oversized file.

**Possible Causes**  
1. Input error - the HAP file path does not exist.  
2. The HAP path is inaccessible.  
3. The HAP size exceeds the 4GB maximum limit.

**Resolution Steps**  
1. Confirm whether the HAP exists.  
2. Check the HAP's executable permissions (readable).  
3. Check whether the HAP size exceeds 4GB.

## 17700015 Application installation failed due to inconsistent configuration information across multiple HAPs

**Error Message**  
Failed to install the HAPs because they have different configuration information.

**Error Description**  
When calling the install interface in the installer module, application installation failed due to inconsistent configuration information across multiple HAPs.

**Possible Causes**  
Fields under the app tag in configuration files of multiple HAPs are inconsistent.

**Resolution Steps**  
Confirm whether fields under the app tag in multiple HAP configuration files are consistent.

## 17700016 Application installation failed due to insufficient system disk space

**Error Message**  
Failed to install the HAP because of insufficient system disk space.

**Error Description**  
When calling the install interface in the installer module, application installation failed due to insufficient system disk space.

**Possible Causes**  
Insufficient system space.

**Resolution Steps**  
Confirm whether the system has sufficient space.

## 17700017 Application installation failed because the new version is lower than the installed version

**Error Message**  
Failed to install the HAP since the version of the HAP to install is too early.

**Error Description**  
When calling the install interface in the installer module, application installation failed because the new version is lower than the installed version.

**Possible Causes**  
The version of the application to be installed is lower than the installed version.

**Resolution Steps**  
Confirm whether the new application version is not lower than the installed version of the same application.

## 17700018 Installation failed due to missing dependent module

**Error Message**  
Failed to install because the dependent module does not exist.

**Error Description**  
When installing HAP, the dependent module does not exist.

**Possible Causes**  
The dependent module is not installed.

**Resolution Steps**  
Install the dependent module first.

## 17700020 Preinstalled application cannot be uninstalled

**Error Message**  
The preinstalled app cannot be uninstalled.

**Error Description**  
When calling the uninstall interface in the installer module to uninstall a preinstalled application, the operation failed.

**Possible Causes**  
1. Incorrect bundleName spelling.  
2. The corresponding preinstalled application cannot be uninstalled.

**Resolution Steps**  
1. Confirm whether bundleName is spelled correctly.  
2. Confirm whether the corresponding preinstalled application can be uninstalled.

## 17700021 Specified uid is invalid

**Error Message**  
The specified uid is invalid.

**Error Description**  
When calling the getBundleNameByUid interface in the bundleManager module, the specified uid is invalid.

**Possible Causes**  
1. Incorrect uid spelling.  
2. The input uid does not exist in the system.

**Resolution Steps**  
1. Verify the uid spelling.  
2. Check whether the uid exists in the system.

## 17700022 Invalid input source file for parsing

**Error Message**  
The input source file is invalid.

**Error Description**  
When calling the getBundleArchiveInfo interface in the bundleManager module, the input HAP path is invalid.

**Possible Causes**  
1. The source file to be parsed does not exist.  
2. The source file to be parsed does not comply with ZIP format.

**Resolution Steps**  
1. Confirm whether the source file to be parsed exists.  
2. Confirm whether the source file complies with ZIP format.

## 17700023 Specified default application does not exist

**Error Message**  
The specified default app does not exist.

**Error Description**  
When calling the getDefaultApplication interface in the defaultAppManager module, the specified default application does not exist.

**Possible Causes**  
The device has not set the corresponding default application.

**Resolution Steps**  
Confirm whether the device has set the corresponding default application.

## 17700024 No corresponding configuration file found

**Error Message**  
The specified profile is not found in the HAP.

**Error Description**  
When calling interfaces to query profile files, no corresponding configuration file was found.

**Possible Causes**  
1. The input metadata name does not exist in the configuration file.  
2. The configuration file content is not in JSON format.  
3. The queried profile type does not exist.

**Resolution Steps**  
1. Confirm whether the metadata name exists in the ability or extensionAbility to be queried.  
2. Confirm whether the specified profile file content is in JSON format.  
3. Confirm whether the application has configuration files matching the queried profileType.

## 17700025 Invalid input type

**Error Message**  
The specified type is invalid.

**Error Description**  
When calling interfaces in the defaultAppManager module, the input type is invalid.

**Possible Causes**  
1. Incorrect type spelling.  
2. The input type does not exist.

**Resolution Steps**  
1. Confirm whether the input type is spelled correctly.  
2. Confirm whether the input type exists.## 17700026 Specified Application Disabled

**Error Message**

The specified bundle is disabled.

**Error Description**

When calling the interface to query application information, the specified application is disabled.

**Possible Causes**

The corresponding application on the device has been disabled and cannot be queried.

**Resolution Steps**

Verify whether the corresponding application on the device is disabled.

## 17700027 Distributed Service Not Running

**Error Message**

The distributed service is not running.

**Error Description**

When calling interfaces related to the distributedBundle module, the distributed service is not running.

**Possible Causes**

The device is not networked.

**Resolution Steps**

Confirm whether the device has successfully joined the network.

## 17700028 Input Ability Does Not Match the Type

**Error Message**

The ability does not match the type.

**Error Description**

When calling the setDefaultApplication interface in the defaultAppManager module, the input ability does not match the type.

**Possible Causes**

The input ability or type is misspelled.

**Resolution Steps**

Verify the spelling of the input ability and type.

## 17700029 Specified Ability Disabled

**Error Message**

The specified ability is disabled.

**Error Description**

When calling the interface to query ability information, the specified ability is disabled.

**Possible Causes**

The specified ability is disabled.

**Resolution Steps**

Check whether the specified ability is disabled. You can use the bm tool command to query the corresponding application information.

## 17700030 Specified Application Does Not Support Clearing Cache Files

**Error Message**

The specified bundle does not support clearing of cache files.

**Error Description**

When calling the cleanBundleCacheFiles interface in the bundleManager module, the specified application does not support clearing cache files.

**Possible Causes**

The specified application is a system application and has the "AllowAppDataNotCleared" field configured in its signing certificate.

**Resolution Steps**

1. Confirm whether the specified application is a system application. Use the bm tool command to query the corresponding application information and check if isSystemApp is true.
2. Confirm whether the specified application has the "AllowAppDataNotCleared" field configured. Use the bm tool command to query the corresponding application information and check if userDataClearable is true.

## 17700031 HAP Installation Failed Due to Overlay Feature Verification Failure

**Error Message**

Failed to install the HAP because the overlay check of the HAP is failed.

**Error Description**

When installing an application with overlay features, the specified application or the overlay feature application to be installed is not a preset application, or the target application/module is an overlay feature application/module.

**Possible Causes**

1. When using inter-application overlay features, the overlay feature application must be a preset application.
2. When using inter-application overlay features, the target application must be a preset application.
3. When using inter-application overlay features, the target application cannot be an overlay feature application.
4. The target module cannot be an overlay feature module.

**Resolution Steps**

1. Check whether the overlay feature application is a preset application.
2. Check whether the target application is a preset application.
3. Check whether the target application is not an overlay feature application.
4. Check whether the target module is not an overlay feature module.

## 17700032 Specified Application Does Not Contain Overlay Feature Module

**Error Message**

The specified bundle does not contain any overlay module.

**Error Description**

When querying the overlayModuleInfo of the overlay feature module in the specified application, the specified application does not contain an overlay feature module.

**Possible Causes**

The specified application does not contain an overlay feature module.

**Resolution Steps**

Check whether the specified application does not contain an overlay feature module.

## 17700033 Specified Module Is Not an Overlay Feature Module

**Error Message**

The specified module is not an overlay module.

**Error Description**

When querying the overlayModuleInfo of the specified overlay feature module, the specified module is not an overlay feature module.

**Possible Causes**

The specified module is not an overlay feature module.

**Resolution Steps**

Check whether the specified module is not an overlay feature module.

## 17700034 Specified Module Is an Overlay Feature Module

**Error Message**

The specified module is an overlay module.

**Error Description**

When querying the overlayModuleInfo associated with the specified target module, the specified module is an overlay feature module.

**Possible Causes**

The specified module is an overlay feature module.

**Resolution Steps**

Check whether the specified module is an overlay feature module.

## 17700035 Specified Application Contains Only Overlay Feature Modules

**Error Message**

The specified bundle is an overlay bundle.

**Error Description**

When querying the overlayModuleInfo associated with the target module of the specified application, the specified application contains only overlay feature modules.

**Possible Causes**

The specified application contains only overlay feature modules.

**Resolution Steps**

Check whether the specified application contains only overlay feature modules.

## 17700036 HSP Installation Failed Due to Missing AllowAppShareLibrary Privilege

**Error Message**

Failed to install the HSP because lacks appropriate permissions.

**Error Description**

The shared library has not applied for the AllowAppShareLibrary privilege, which may pose security and privacy risks and is not allowed for installation.

**Possible Causes**

Before releasing the shared library, the AllowAppShareLibrary privilege was not applied for or configured.

**Resolution Steps**

Apply for the AllowAppShareLibrary privilege for the shared library, re-sign, and release it.

## 17700037 Uninstalled Shared Library Version Is Dependent on Other Applications

**Error Message**

The version of shared bundle is dependent on other applications.

**Error Description**

When uninstalling a version of the shared library, the specified version of the shared library is dependent on other applications, resulting in uninstallation failure.

**Possible Causes**

1. The version being uninstalled is the highest version of the shared library, and this shared library is dependent on other applications.
2. The version of the shared library is not specified during uninstallation, which would uninstall all versions of the shared library, and this shared library is dependent on other applications.

**Resolution Steps**

1. Check whether the shared library being uninstalled is dependent on other applications.
2. Check whether the version being uninstalled is the highest version of the shared library.

## 17700038 Specified Shared Library Does Not Exist

**Error Message**

The specified shared bundle does not exist.

**Error Description**

When uninstalling a shared library, the specified shared library does not exist.

**Possible Causes**

1. The version specified for uninstallation does not exist in the shared library to be uninstalled.
2. The shared library specified for uninstallation does not exist on the device.

**Resolution Steps**

1. Check whether the shared library to be uninstalled exists on the current device.
2. Check whether the version to be uninstalled exists in the shared library to be uninstalled.

## 17700039 Installation of Inter-Application Shared Library Not Allowed

**Error Message**

Failed to install because disallow install a shared bundle by hapFilePaths.

**Error Description**

When installing an application, the installation package passed is of the inter-application shared library type.

**Possible Causes**

1. When using the bm tool to install an application, the -p parameter passed the installation path of an inter-application shared library.
2. When using the install interface to install an application, the hapFilePaths parameter passed the installation path of an inter-application shared library.

**Resolution Steps**

1. Use the -s parameter to specify the installation path of the inter-application shared library.
2. Use the sharedBundleDirPaths field in the installParam parameter to specify the installation path of the inter-application shared library.

## 17700040 Uninstallation of Inter-Application Shared Library Not Allowed

**Error Message**

The specified bundle is a shared bundle which cannot be uninstalled.

**Error Description**

When uninstalling an application, the package name passed is of an inter-application shared library.

**Possible Causes**

1. When using the bm tool to uninstall an application, the -n parameter passed the package name of an inter-application shared library.
2. When using the uninstall interface to uninstall an application, the bundleName passed is the package name of an inter-application shared library.

**Resolution Steps**

1. Use the -s parameter to specify that the application to be uninstalled is a shared library application.
2. Use the bundleName and versionCode fields in the UninstallParam parameter to specify the package name and version of the shared library to be uninstalled.

## 17700041 Enterprise Device Management Disallows Installation of the Application

**Error Message**

Failed to install because enterprise device management disallow install.

**Error Description**

When installing an application, enterprise device management does not allow the installation.

**Possible Causes**

Enterprise device management does not allow the installation of the application.

**Resolution Steps**

Check on the device whether the application is blocked from installation by enterprise device management.

## 17700042 Incorrect URI Configuration in Data Proxy

**Error Message**

Failed to install the HAP because of incorrect URI in the data proxy.

**Error Description**

When installing an application, the URI configuration in the data proxy is incorrect.

**Possible Causes**

1. The package name in the URI does not match the current application's package name.
2. The URI is duplicated.

**Resolution Steps**

1. Modify the package name in the URI to match the current application's package name.
2. Modify the duplicated URI. Each data proxy URI must be unique.

## 17700043 Incorrect Permission Configuration in Data Proxy

**Error Message**

Failed to install the HAP because of low APL in the non-system data proxy (required APL: system_basic or system_core).

**Error Description**

When installing an application, the permission level of the non-system application's data proxy is too low. It should be system_basic or system_core.

**Possible Causes**

1. The non-system application's data proxy does not have permissions configured.
2. The permission level of the non-system application's data proxy is too low.

**Resolution Steps**

1. Configure read and write permissions in the data proxy.
2. Modify the read and write permissions and ensure their level is system_basic or system_core.

## 17700044 Contradiction Between Multi-Process Configuration in Installation Package and System Configuration

**Error Message**

Failed to install the HAP because the isolationMode configured is not supported.

**Error Description**

When installing an application, the configured isolationMode contradicts the system configuration allowed by the system.

**Possible Causes**

1. When the device supports isolation mode (i.e., persist.bms.supportIsolationMode is true), the HAP's configured isolationMode is nonisolationOnly.
2. When the device does not support isolation mode (i.e., persist.bms.supportIsolationMode is false), the HAP's configured isolationMode is isolationOnly.

**Resolution Steps**

Correctly configure the HAP's isolationMode field according to the device's isolation mode.

## 17700045 Enterprise Device Management Disallows Uninstallation of the Application

**Error Message**

Failed to uninstall because enterprise device management disallow uninstall.

**Error Description**

When uninstalling an application, enterprise device management does not allow the uninstallation.

**Possible Causes**

Enterprise device management does not allow the uninstallation of the application.

**Resolution Steps**

Check on the device whether the application is blocked from uninstallation by enterprise device management.

## 17700047 Version to Be Updated Is Not Greater Than the Current Version

**Error Message**

Failed to install the HAP because the VersionCode to be updated is not greater than the current VersionCode.

**Error Description**

When installing an application, the version to be updated is not greater than the current version.

**Possible Causes**

1. The version number of the installation package is less than or equal to the version number of the installed application.
2. The installFlag is set to NORMAL, in which case the version number of the application to be updated must be greater than the currently installed version.

**Resolution Steps**

1. Set the application's version number to be greater than the current version.
2. If you want to update the application without upgrading the version number, set the installFlag to REPLACE_EXISTING.## 17700048 Code Signature Verification Failed

**Error Message**

Failed to install the HAP because the code signature verification is failed.

**Error Description**

During application installation, the code signature file verification of the installation package failed.

**Possible Causes**

1. The module corresponding to the code signature file does not exist in the installation package.
2. The code signature file path is invalid.
3. The code signature file does not match the corresponding installation package.

**Resolution Steps**

1. Verify that the module corresponding to the code signature file is included in the installation package path.
2. Check whether the provided code signature file path is valid.
3. Use a code signature file that matches the installation package.

## 17700049 Mismatched Bundle Names During Application Self-Upgrade

**Error Message**

Failed to install the HAP because the bundleName is different from the bundleName of the caller application.

**Error Description**

During enterprise MDM application self-upgrade, the installed application's bundle name differs from the caller application's bundle name.

**Possible Cause**

The HAP to be installed does not belong to the current application.

**Resolution Steps**

Verify whether the HAP to be installed belongs to the current application.

## 17700050 Enterprise Device Verification Failed

**Error Message**

Failed to install the HAP because enterprise normal/MDM bundle cannot be installed on non-enterprise device.

**Error Description**

During application installation, enterprise normal applications or enterprise MDM applications cannot be installed on non-enterprise devices.

**Possible Cause**

The installation device is not an enterprise device.

**Resolution Steps**

1. Verify whether the installation device is an enterprise device.
2. Check whether the device parameter `const.bms.allowenterprisebundle` is set to `true`.

## 17700051 Caller Application Distribution Type Mismatch During Self-Upgrade

**Error Message**

Failed to install the HAP because the distribution type of caller application is not enterprise_mdm.

**Error Description**

During enterprise MDM application self-upgrade, the caller application's distribution type is not enterprise_mdm.

**Possible Cause**

The caller application's distribution type is not enterprise_mdm.

**Resolution Steps**

Verify whether the application's signature file is correctly configured.

## 17700052 Debug Bundle Installation Not Allowed in Non-Developer Mode

**Error Message**

Failed to install the HAP because debug bundle cannot be installed under non-developer mode.

**Error Description**

When installing a debug application, the device is in non-developer mode, which prohibits installation.

**Possible Cause**

The application is a debug application, but the device is in non-developer mode.

**Resolution Steps**

Execute `hdc shell param get const.security.developermode.state`. If the returned result is `false`, the device cannot install debug applications.

## 17700053 Non-AppGallery Call

**Error Message**

Not app gallery call.

**Error Description**

Non-AppGallery application call. This interface is exclusively for AppGallery calls.

**Possible Cause**

The caller is not AppGallery.

**Resolution Steps**

Verify whether the caller is AppGallery.

## 17700054 Permission Verification Failure Causes Installation Failure

**Error Message**

Failed to install the HAP because the HAP requests wrong permissions.

**Error Description**

The application to be installed requested incorrect permissions, resulting in installation failure.

**Possible Causes**

1. A non-MDM application requested MDM-type permissions.
2. The application's permission level is lower than the requested permission level.

**Resolution Steps**

1. Check whether MDM-type permissions were requested. MDM-type permissions are only available for applications of the MDM type.
2. Verify whether the requested permission level is higher than the application's permission level. Since the default application level is `normal`, only `normal`-level permissions can be used. If `system_basic` or `system_core`-level permissions are used, an error will occur. Modify the `apl` level in the `UnsgnedDebugProfileTemplate.json` file to `system_basic` or `system_core`, then re-sign and repackage the application.

## 17700055 Invalid Specified Link

**Error Message**

The specified link is invalid.

**Error Description**

When calling the `canOpenLink` interface in the `bundleManager` module, the specified link is invalid.

**Possible Cause**

The input link format is incorrect.

**Resolution Steps**

Verify whether the link format is correct.

## 17700056 Specified Link Scheme Not Configured in querySchemes Field

**Error Message**

The scheme of the specified link is not in the querySchemes.

**Error Description**

When calling the `canOpenLink` interface in the `bundleManager` module, the specified link's scheme is not configured in the `querySchemes` field.

**Possible Cause**

The specified link's scheme is not configured in the `querySchemes` field.

**Resolution Steps**

Check whether the corresponding URL scheme is configured in the `querySchemes` field.

## 17700201 ABC File Verification Failed

**Error Message**

Failed to verify abc.

**Error Description**

The .abc file path verification failed.

**Possible Cause**

The .abc file is untrusted.

**Resolution Steps**

Provide a trusted .abc file path.

## 17700202 ABC File Deletion Failed

**Error Message**

Failed to delete abc.

**Error Description**

The .abc file deletion failed.

**Possible Cause**

The .abc file does not exist.

**Resolution Steps**

Provide a valid .abc file path.