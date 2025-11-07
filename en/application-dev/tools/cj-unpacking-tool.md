# Unpacking Tool

The unpacking tool is a debugging utility provided by OpenHarmony that supports decompressing HAP, HSP, and App files into folders via command-line interface, and offers Java APIs for parsing these files.

The app_unpacking_tool.jar used for unpacking can be found in the locally downloaded OpenHarmony SDK library.

> **Note:**
>
> Currently, Cangjie only supports developing HAR and HAP packages, not HSP packages. Therefore, HSP-related functionalities in this tool are unavailable in Cangjie programs.

## Constraints and Limitations

The unpacking tool requires Java 8 or higher to run.

## Unpacking Command Instructions

### HAP Package Mode Unpacking Command

Developers can use the unpacking tool's JAR package to unpack applications by specifying unpacking options and file paths to extract HAP packages.

#### Example

```bash
java -jar app_unpacking_tool.jar --mode hap --hap-path <path> --out-path <path> [--force true]
```

#### Parameter Descriptions and Specifications

| Command      | Required    | Options        | Description                                                                                  |
|--------------|-------------|----------------|----------------------------------------------------------------------------------------------|
| --mode       | Yes         | hap            | Unpacking type.                                                                              |
| --hap-path   | Yes         | NA             | Path to the HAP package.                                                                     |
| --rpcid      | No          | true or false  | Whether to extract only the rpcid file from the HAP package to the specified directory. If true, only the rpcid file will be extracted without unpacking the HAP package. |
| --out-path   | Yes         | NA             | Target directory path for unpacking.                                                         |
| --force      | No          | true or false  | Default is false. If true, forces deletion when the target file already exists.              |

### App Package Mode Unpacking Command

Developers can use the unpacking tool's JAR package to unpack applications by specifying unpacking options and file paths to extract App packages.

#### Example

```bash
java -jar app_unpacking_tool.jar --mode app --app-path <path> --out-path <path> [--force true]
```

#### Parameter Descriptions and Specifications

| Command      | Required    | Options        | Description                                                                 |
|--------------|-------------|----------------|-----------------------------------------------------------------------------|
| --mode       | Yes         | app            | Unpacking type.                                                             |
| --app-path   | Yes         | NA             | Path to the App package.                                                    |
| --out-path   | Yes         | NA             | Target directory path for unpacking.                                        |
| --force      | No          | true or false  | Default is false. If true, forces deletion when the target file already exists. |

### Extracting rpcid File from HAP Package

Developers can use the unpacking tool's JAR package to unpack applications by specifying unpacking options and file paths to retrieve the application's rpcid.

#### Example

```bash
java -jar app_unpacking_tool.jar --mode hap --rpcid true --hap-path <path> --out-path <path> [--force true]
```

#### Parameter Descriptions and Specifications

| Command      | Required    | Options        | Description                                                                                  |
|--------------|-------------|----------------|----------------------------------------------------------------------------------------------|
| --mode       | Yes         | hap            | Unpacking type.                                                                              |
| --rpcid      | No          | true or false  | Whether to extract only the rpcid file from the HAP package to the specified directory. If true, only the rpcid file will be extracted without unpacking the HAP package. |
| --hap-path   | Yes         | NA             | Path to the HAP package.                                                                     |
| --out-path   | Yes         | NA             | Target directory path for the rpcid file.                                                    |
| --force      | No          | true or false  | Default is false. If true, forces deletion when the target file already exists.              |

### HSP Package Mode Unpacking Command

Developers can use the unpacking tool's JAR package to unpack applications by specifying unpacking options and file paths to extract HSP packages.

#### Example

```bash
java -jar app_unpacking_tool.jar --mode hsp --hsp-path <path> --out-path <path> [--force true]
```

#### Parameter Descriptions and Specifications

| Command      | Required    | Options        | Description                                                                 |
|--------------|-------------|----------------|-----------------------------------------------------------------------------|
| --mode       | Yes         | hsp            | Unpacking type.                                                             |
| --hsp-path   | Yes         | NA             | Path to the HSP package.                                                    |
| --out-path   | Yes         | NA             | Target directory path for unpacking.                                        |
| --force      | No          | true or false  | Default is false. If true, forces deletion when the target file already exists. |

### APPQF Mode Unpacking Command

Developers can use the unpacking tool's JAR package to unpack applications by specifying unpacking options and file paths to extract APPQF packages.

#### Example

```bash
java -jar app_unpacking_tool.jar --mode appqf --appqf-path <path> --out-path <path> [--force true]
```

#### Parameter Descriptions and Specifications

| Command      | Required    | Options        | Description                                                                 |
|--------------|-------------|----------------|-----------------------------------------------------------------------------|
| --mode       | Yes         | appqf          | Unpacking type.                                                             |
| --appqf-path | Yes         | NA             | Path to the APPQF package.                                                  |
| --out-path   | Yes         | NA             | Target directory path for unpacking.                                        |
| --force      | No          | true or false  | Default is false. If true, forces deletion when the target file already exists. |

## Package Parsing APIs

The package parsing APIs are exclusively used by app stores to parse built HAP, HSP, and App packages to retrieve configuration file information.

### API Directory

| Class Name          | API Prototype                                                                 | Type     | Detailed Description                                                                 |
|----------------------|-------------------------------------------------------------------------------|----------|-------------------------------------------------------------------------------------|
| UncompressEntrance   | UncompressResult parseApp(String appPath, ParseAppMode parseMode, String hapName) | Java API | Function: Parses the pack.info information of an App package based on parameters.<br/>Input: appPath (App package path), parseMode (parsing mode enum: ALL/HAP_LIST/HAP_INFO), hapName (HAP package name, required when parseMode is HAP_INFO).<br/>Return: UncompressResult. |
| UncompressEntrance   | UncompressResult parseApp(InputStream input, ParseAppMode parseMode, String hapName) | Java API | Function: Parses the pack.info information of an App package based on parameters.<br/>Input: input (App file stream), parseMode (parsing mode enum: ALL/HAP_LIST/HAP_INFO), hapName (HAP package name, required when parseMode is HAP_INFO).<br/>Return: UncompressResult. |
| UncompressEntrance   | UncompressResult parseHap(String hapPath)                                    | Java API | Function: Parses the JSON configuration file of an App package based on parameters.<br/>Input: hapPath (HAP package path).<br/>Return: UncompressResult. |
| UncompressEntrance   | UncompressResult parseHap(InputStream input)                                 | Java API | Function: Parses the JSON configuration file of an App package based on parameters.<br/>Input: input (HAP package file stream).<br/>Return: UncompressResult. |

## Unpacking Tool Information Fields

### UncompressResult (Bundle Information) Structure

| Field            | Type               | Description                                                                 | Note |
|------------------|--------------------|-----------------------------------------------------------------------------|------|
| result           | boolean            | Indicates whether the parsing was successful. true for success, false for failure. | NA   |
| message          | String             | Reason for failure if parsing fails.                                        | NA   |
| packInfos        | List\<PackInfo>    | packages information from the pack.info file in the bundle.                 | NA   |
| profileInfos     | List\<ProfileInfo> | Application configuration information.                                      | NA   |
| profileInfosStr  | List\<String>      | Application configuration information.                                      | NA   |
| icon             | String             | Path to the entry component's icon. If no entry component exists, returns the first component's icon. | NA   |
| label            | String             | Label of the entry component. If no entry component exists, returns the first component's label. | NA   |
| packageSize      | long               | Size of the App package in bytes.                                           | NA   |

### PackInfo Structure

| Field                | Type          | Description                                                                 | Note |
|----------------------|---------------|-----------------------------------------------------------------------------|------|
| name                 | String        | Package name.                                                              | NA   |
| moduleName           | String        | HAP name.                                                                  | NA   |
| moduleType           | String        | Type of the module.                                                         | NA   |
| deviceType           | List\<String> | Device types supported by the current HAP package.                         | NA   |
| deliveryWithInstall  | boolean       | Indicates whether the current HAP is installed during user-initiated installation. true for installation, false otherwise. | NA   |

### ProfileInfo Structure

| Field          | Type                           | Description                                                                 | Note                                                                                         |
|----------------|--------------------------------|-----------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|
| hapName        | String                         | Name of the current HAP package being parsed.                               | NA                                                                                           |
| appInfo        | AppInfo structure (see below)  | Structure containing App information (see AppInfo below).                   | NA                                                                                           |
| deviceConfig   | Map\<String, DeviceConfig>    | Device information.                                                        | Stored as Map\<String, String>, containing device type names and corresponding information. In the stage model, this field is stored in the app structure. |
| hapInfo        | HapInfo structure (see below)  | Module information in the HAP package (see HapInfo below).                 | NA                                                                                           |

### AppInfo Structure

| Field                           | Type                  | Description                                                                 | Note                                                                 |
|---------------------------------|-----------------------|-----------------------------------------------------------------------------|---------------------------------------------------------------------|
| bundleName                      | String                | Name of the App package.                                                    | NA                                                                  |
| vendor                          | String                | Vendor information of the App.                                             | NA                                                                  |
| relatedBundleName               | String                | Name of the related bundle package.                                        | NA                                                                  |
| versionName                     | String                | versionName information in the App.                                         | NA                                                                  |
| versionCode                     | String                | versionCode information in the App.                                         | NA                                                                  |
| targetApiVersion                | int                   | Target API version required for the application to run.                     | NA                                                                  |
| compatibleApiVersion            | int                   | Compatible API version of the application.                                  | NA                                                                  |
| appName                         | String                | Label displayed on the desktop for the ability.                             | NA                                                                  |
| appNameEN                       | String                | Label displayed on the desktop for the ability.                             | NA                                                                  |
| releaseType                     | String                | Type of the target API version required for the application to run.         | NA                                                                  |
| shellVersionCode                | String                | API version number of the application.                                      | NA                                                                  |
| shellVersionName                | String                | API version name of the application.                                        | NA                                                                  |
| multiFrameworkBundle            | boolean               | Application framework. true for hybrid packaging, false otherwise.          | NA                                                                  |
| debug                           | boolean               | Whether the application is debuggable. true for debuggable, false otherwise. | NA                                                                  |
| icon                            | String                | Path to the application's icon.                                            | NA                                                                  |
| label                           | String                | Label of the application.                                                   | NA                                                                  |
| description                     | String                | Description of the application.                                             | Added in the stage model.                                           |
| minCompatibleVersionCode        | int                   | Minimum compatible version number of the application.                        | NA                                                                  |
| distributedNotificationEnabled  | boolean               | Whether distributed notifications are enabled for the application. true for enabled, false otherwise. | Added in the stage model.                                           |
| bundleType                      | String                | Type of the bundle. Values:<br/>- app: Application.<br/>- atomicService: Atomic service.<br/>- shared: Shared library between applications. | NA                                                                  |
| compileSdkVersion               | String                | SDK version used to compile the application.                                | Only for applications with API 10 or later.                         |
| compileSdkType                  | String                | SDK category used to compile the application.                               | Only for applications with API 10 or later.                         |
| labels                          | HashMap\<String, String> | Multi-language labels for the AppJson application.                          | NA                                                                  |
| descriptions                    | HashMap\<String, String> | Multi-language descriptions for the AppJson application.                    | NA                                                                  |

### HapInfo Structure

| Field                 | Type                        | Description                                                                 | Note                                                                 |
|-----------------------|-----------------------------|-----------------------------------------------------------------------------|---------------------------------------------------------------------|
| appModel              | AppModel enum               | Framework model of the application.<br/>- FA: FA model.<br/>- STAGE: Stage model. | NA                                                                  |
| packageStr            | String                      | Package information of the application.                                     | Specific to the FA model.                                           |
| name                  | String                      | Name of the current module.                                                | NA                                                                  |
| description           | String                      | Description of the HAP package.                                            | Specific to the FA model.                                           |
| supportedModes        | List\<String>               | Supported modes of the HAP package.                                        | NA                                                                  |
| abilities             | List\<AbilityInfo>          | Ability information in the HAP package.                                    | NA                                                                  |
| defPermissions        | List\<DefPermission>        | DefPermission information in the HAP package.                             | NA                                                                  |
| definePermissions     | List\<DefinePermission>     | DefinePermission information in the HAP package.                           | NA                                                                  |
| defPermissionsGroups  | List\<DefPermissionsGroups> | DefPermissionsGroups information in the HAP package.                      | NA                                                                  |
| distro                | Distro structure            | Distro information of the HAP package.                                    | NA                                                                  |
| reqCapabilities       | List\<String>               | reqCapabilities information in the HAP package.                            | NA                                                                  |
| deviceType            | List\<String>               | Device types on which the HAP can run.                                    | Corresponds to deviceTypes in the stage model.                      |
| metaData              | MetaData structure (see below) | Custom metadata of the HAP.                                               | NA                                                                  |
| dependencies          | List\<DependencyItem>       | DependencyItem information in the HAP package.                             | NA                                                                  |
| isJs                  | boolean                     | Whether the application is a JS application. true for JS, false otherwise. | Specific to the FA model.                                           |
| reqPermissions        | List\<ReqPermission>        | Collection of permissions requested by the application.                    | Corresponds to requestPermissions in the stage model.               |
| commonEvents          | CommonEvent structure (see below) | Static events.                                                            | NA                                                                  |
| shortcuts             | List\<Shortcut>             | Shortcuts information of the application.                                  | NA                                                                  |
| distroFilter          | DistroFilter structure      | Information for app store distribution by device type.                     | NA                                                                  |
| srcEntrance           | String                      | Entry code path of the application.                                       | Added in the stage model.                                           |
| process               | String                      | Process name of the HAP.                                                  | Added in the stage model.                                           |
| mainElement           | String                      | Name of the entry ability or extension in the HAP.                         | Added in the stage model. In the FA model, mainAbility value is assigned to mainElement. |
| uiSyntax              | String                      | Syntax type of the JS Component.                                          | Added in the stage model.                                           |
| pages                 | List\<String>               | Page information in the JS Component.                                     | Added in the stage model.                                           |
| extensionAbilityInfos | List\<ExtensionAbilityInfo> | Configuration information of extensionAbility.                             | Added in the stage model.                                           |
| moduleAtomicService   | ModuleAtomicService structure (see below) | Atomic service information of the HAP.                                    | NA                                                                  |
| formInfos             | List\<AbilityFormInfo>      | Card information.                                                         | NA                                                                  |
| descriptions          | HashMap\<String, String>    | Description information of the HAP.                                       | NA                                                                  |
| compressedSize        | long                        | Compressed size of the HAP package in bytes.                              | NA                                                                  |
| originalSize          | long                        | Original size of the HAP package in bytes.                                | NA                                                                  |

### AbilityInfo Structure

| Field              | Type                       | Description                                                                 | Note                                                                 |
|--------------------|----------------------------|-----------------------------------------------------------------------------|---------------------------------------------------------------------|
| name               | String                     | Logical name of the current ability.                                        | NA                                                                  |
| description        | String                     | Description of the ability.                                                | NA                                                                  |
| descriptionRes     | String                     | Resource description of the ability.                                        | NA                                                                  |
| icon               | String                     | Icon of the ability.                                                       | NA                                                                  |
| iconPath           | String                     | Path to the ability's icon.                                                | NA                                                                  |
| label              | String                     | Name displayed to users for the ability.                                   | NA                                                                  |
| labelRes           | String                     | Resource name displayed to users for the ability.                          | NA                                                                  |
| type               | String                     | Type of the ability.                                                       | In the stage model, this value is directly assigned as page type.  |
| formsEnabled       | boolean                    | Whether the ability's card is enabled. true for enabled, false otherwise.  | NA                                                                  |
| formInfo           | FormInfo structure          | Card information.                                                          | NA                                                                  |
| uri                | String                     | URI information of the ability.                                            | Supported in the FA model.                                          |
| launchType         | String                     | launcherType information of the ability.                                   | NA                                                                  |
| orientation        | String                     | orientation information of the ability.                                    | NA                                                                  |
| visible            | boolean                    | visible information of the ability. true for visible, false otherwise.    | NA                                                                  |
| grantPermission    | boolean                    | grantPermission information of the ability.                                | NA                                                                  |
| readPermission     | String                     | readPermission information of the ability.                                | NA                                                                  |
| writePermission    | String                     | writePermission information of the ability.                                | NA                                                                ### UriInfo Structure Information

| Field          | Type   | Description                          | Remarks |
| -------------- | ------ | ------------------------------------ | ------- |
| schema         | String | Identifies the schema information of ModuleUriInfo. | NA      |
| host           | String | Identifies the host information of ModuleUriInfo. | NA      |
| port           | String | Identifies the port information of ModuleUriInfo. | NA      |
| pathStartWith  | String | Identifies the path prefix of ModuleUriInfo. | NA      |
| pathRegex      | String | Identifies the regular expression for the path of ModuleUriInfo. | NA      |
| path           | String | Identifies the path information of ModuleUriInfo. | NA      |
| type           | String | Identifies the type of ModuleUriInfo. | NA      |

### AbilityFormInfo Structure Information

| Field                  | Type                     | Description                                                                 | Remarks |
| ---------------------- | ------------------------ | --------------------------------------------------------------------------- | ------- |
| name                   | String                   | Identifies the name of the form.                                            | NA      |
| type                   | String                   | Identifies the type of the card.                                            | NA      |
| updateEnabled          | boolean                  | Indicates whether the card supports scheduled refresh. `true` means supported, `false` means not supported. | NA      |
| scheduledUpdateTime    | String                   | Specifies the scheduled refresh time of the card, using 24-hour format with minute precision. | NA      |
| updateDuration         | int                      | Specifies the refresh interval of the card, in units of 30 minutes (must be a multiple of 30). | NA      |
| supportDimensions      | List\<String>            | Specifies the appearance specifications of the card, with values such as "1 * 2", "2 * 2", "2 * 4", "4 * 4". | NA      |
| defaultDimension       | String                   | Specifies the default appearance specification of the card, which must be one of the values in `supportDimensions`. | NA      |
| MetaData               | MetaData                 | Identifies custom information for the card.                                 | NA      |
| description            | String                   | Identifies the description of the form.                                     | Added in Stage model. |
| src                    | String                   | Specifies the UI code for the JS card.                                      | NA      |
| windowInfo             | ModuleWindowInfo struct  | Specifies the window for the ability form.                                  | NA      |
| isDefault              | boolean                  | Indicates whether the card is the default card. Each HAP can have only one default card. `true` means default, `false` means non-default. | NA      |
| colorMode              | String                   | Specifies the color mode of the card, with values `auto`, `dark`, or `light`. | NA      |
| formConfigAbility      | String                   | Identifies the Ability name for card configuration.                         | NA      |
| formVisibleNotify      | String                   | Indicates whether the card is allowed to use visibility notifications.      | NA      |
| providerAbility        | String                   | Specifies the Ability or Extension name where the card provider resides.<br/>1. FA model: If the card is configured in a service-type Ability, `providerAbility` is set to `mainAbility`.<br/>2. FA model: If the card is configured in a page-type Ability, `providerAbility` is set to the current Ability.<br/>3. FA model: If `mainAbility` is not configured, `providerAbility` is set to `system.home` if available; otherwise, the first page-type Ability in the HAP.<br/>4. Stage model (follows the above rules), `providerAbility` is set to `mainElement`. | NA |
| descriptions           | HashMap\<String, String> | Identifies the description of the Ability in multiple languages.             | NA      |

### CommonEvent Structure Information

| Field        | Type           | Description                                                                 | Remarks |
| ------------ | -------------- | --------------------------------------------------------------------------- | ------- |
| name         | String         | Specifies the class name of the current static common event.                | Retrieved from `staticSubscriber`-type Extension in Stage model. |
| permission   | String         | Specifies the permission required to implement the static common event.     | Retrieved from `staticSubscriber`-type Extension in Stage model. |
| data         | List\<String>  | Specifies the additional data array required for the current static common event. | Retrieved from `staticSubscriber`-type Extension in Stage model. |
| type         | List\<String>  | Specifies the category array for the current static common event.            | Retrieved from `staticSubscriber`-type Extension in Stage model. |
| events       | List\<String>  | Specifies the set of intent event values that can be received.               | Retrieved from `staticSubscriber`-type Extension in Stage model. |

### DependencyItem Structure Information

| Field         | Type   | Description                          | Remarks |
| ------------- | ------ | ------------------------------------ | ------- |
| bundleName    | String | Specifies the bundleName of the shared package. | NA      |
| moduleName    | String | Specifies the moduleName of the shared package. | NA      |
| versionCode   | String | Specifies the version code of the shared package. | NA      |

### ModuleAtomicService Structure Information

| Field         | Type                | Description              | Remarks |
| ------------- | ------------------- | ------------------------ | ------- |
| preloadItems  | list\<PreloadItem>  | Specifies preload objects. | NA      |

### PreloadItem Structure Information

| Field       | Type   | Description                | Remarks |
| ----------- | ------ | -------------------------- | ------- |
| moduleName  | String | Specifies the module name to preload. | NA      |

### DeviceConfig Structure Information

| Field                          | Type    | Description                                                                 | Remarks |
| ------------------------------ | ------- | --------------------------------------------------------------------------- | ------- |
| targetReqSdk                   | String  | Specifies the target requested SDK version for the application's DeviceConfig. | NA      |
| compatibleReqSdk               | String  | Specifies the compatible requested SDK version for the application's DeviceConfig. | NA      |
| jointUserid                    | String  | Specifies the jointUserid for the application's DeviceConfig.               | NA      |
| process                        | String  | Specifies the process for the application's DeviceConfig.                   | NA      |
| arkFlag                        | String  | Specifies the arkFlag for the application's DeviceConfig.                   | NA      |
| targetArkVersion               | String  | Specifies the target ArkVersion for the application's DeviceConfig.         | NA      |
| compatibleArkVersion           | String  | Specifies the compatible ArkVersion for the application's DeviceConfig.     | NA      |
| directLaunch                   | boolean | Indicates whether the application's DeviceConfig supports direct launch.    | NA      |
| distributedNotificationEnabled | boolean | Indicates whether distributed notifications are enabled for the application's AppJson. `true` means enabled, `false` means disabled. | NA      |

### DefPermission Structure Information

| Field           | Type                     | Description                                      | Remarks |
| --------------- | ------------------------ | ------------------------------------------------ | ------- |
| name            | String                   | Specifies the name of the DefPermission.         | NA      |
| grantMode       | String                   | Specifies the grantMode of the DefPermission.    | NA      |
| group           | String                   | Specifies the group of the DefPermission.        | NA      |
| label           | String                   | Specifies the label of the DefPermission.        | NA      |
| description     | String                   | Specifies the description of the DefPermission.  | NA      |
| availableScope  | List\<String>            | Specifies the available scope of the DefPermission. | NA      |
| labels          | HashMap\<String, String> | Specifies the labels of the DefPermission in multiple languages. | NA      |
| descriptions    | HashMap\<String, String> | Specifies the descriptions of the DefPermission in multiple languages. | NA      |

### DefinePermission Structure Information

| Field                   | Type                     | Description                                                                 | Remarks |
| ----------------------- | ------------------------ | --------------------------------------------------------------------------- | ------- |
| name                    | String                   | Specifies the name of the DefinePermission.                                 | NA      |
| grantMode               | String                   | Specifies the grantMode of the DefinePermission.                            | NA      |
| availableLevel          | String                   | Specifies the group of the DefinePermission.                                | NA      |
| provisionEnable         | boolean                  | Indicates whether the module-defined permission supports certificate-based application. `true` means supported, `false` means not supported. | NA      |
| distributedSceneEnable  | boolean                  | Indicates whether the ModuleDefinePermission supports distributed scenarios. `true` means supported, `false` means not supported. | NA      |
| label                   | String                   | Specifies the label of the DefinePermission.                                | NA      |
| description             | String                   | Specifies the description of the DefinePermission.                           | NA      |
| descriptions            | HashMap\<String, String> | Specifies the descriptions of the DefinePermission in multiple languages.   | NA      |
| labels                  | HashMap\<String, String> | Specifies the labels of the DefinePermission in multiple languages.        | NA      |

### DefPermissionsGroups Structure Information

| Field       | Type    | Description                          | Remarks |
| ----------- | ------- | ------------------------------------ | ------- |
| name        | String  | Specifies the name of the DefPermissionGroup. | NA      |
| order       | String  | Specifies the order of the DefPermissionGroup. | NA      |
| icon        | String  | Specifies the icon of the DefPermissionGroup. | NA      |
| label       | String  | Specifies the label of the DefPermissionGroup. | NA      |
| description | String  | Specifies the description of the DefPermissionGroup. | NA      |
| request     | boolean | Specifies the request of the DefPermissionGroup. | NA      |

### FormInfo Structure Information

| Field          | Type           | Description                          | Remarks |
| -------------- | -------------- | ------------------------------------ | ------- |
| formEntity     | List\<String>  | Specifies the formEntity of the formInfo. | NA      |
| minHeight      | String         | Specifies the minimum height of the formInfo. | NA      |
| defaultHeight  | String         | Specifies the default height of the formInfo. | NA      |
| minWidth       | String         | Specifies the minimum width of the formInfo. | NA      |
| defaultWidth   | String         | Specifies the default width of the formInfo. | NA      |

### ModuleMetadataInfo Structure Information

| Field    | Type   | Description                          | Remarks |
| -------- | ------ | ------------------------------------ | ------- |
| name     | String | Specifies the name of the ModuleMetadataInfo. | NA      |
| value    | String | Specifies the value of the ModuleMetadataInfo. | NA      |
| resource | String | Specifies the resource of the ModuleMetadataInfo. | NA      |

### ModuleWindowInfo Structure Information

| Field            | Type    | Description                          | Remarks |
| ---------------- | ------- | ------------------------------------ | ------- |
| designWidth      | int     | Specifies the design width for the module's used scenario. | NA      |
| autoDesignWidth  | boolean | Specifies the autoDesignWidth of ModuleUsedScene. | NA      |