# Application Sandbox Directory

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

The application sandbox is an isolation mechanism designed for security protection, preventing data from being accessed via malicious path traversal. Under this sandbox protection mechanism, the directory scope visible to an application is referred to as the "Application Sandbox Directory."

- For each application, the system maps a dedicated "Application Sandbox Directory" in the internal storage space. It is a collection of the "[Application File Directory](#application-file-directory-and-application-file-path)" and a subset of system files (a minimal set of system files required for the application to run).

- The application sandbox restricts the data scope visible to the application. Within the "Application Sandbox Directory," an application can only see its own files and a minimal set of system files (required for its operation). Consequently, files from this application are also invisible to other applications, thereby safeguarding application file security.

- Applications can save and manage their files in the "Application File Directory"; system files and their directories are read-only to applications. To access [user files](./cj-user-file-overview.md), applications must use specific APIs and obtain corresponding user authorization.

The diagram below illustrates the file access scope and methods available to applications under the sandbox.

![Application sandbox file access relationship](figures/application-sandbox-file-access-relationship.png)

## Application Sandbox Directory and Sandbox Path

Under the application sandbox protection mechanism, applications cannot determine the location or existence of data directories belonging to other applications or users outside their own application file directory. Additionally, all application directory visibility scopes are isolated through permission and file path mounting, forming an independent path view that masks the actual physical paths.

- As shown below, from the perspective of a regular application (also called a third-party application), not only is the scope of visible directories and files limited, but the visible directory and file paths also differ from those seen by system processes or other processes. The path of a file or specific directory under the "Application Sandbox Directory" as seen by a regular application is referred to as the "Application Sandbox Path."<!--RP1-->
- The developer's `hdc shell` environment is equivalent to the system process perspective. Therefore, the "Application Sandbox Path" differs from the actual physical path seen when debugging with the `hdc` tool. For specific mappings, refer to [Correspondence Between Application Sandbox Path and Actual Physical Path](#correspondence-between-application-sandbox-path-and-actual-physical-path).<!--RP1End-->
- The actual physical path and sandbox path do not have a 1:1 mapping relationship. Sandbox paths are always fewer than the physical paths visible from the system process perspective. Some physical paths visible from the debugging process perspective have no corresponding path in the application sandbox directory.

![Application sandbox path](figures/application-sandbox-path.png)

## Application File Directory and Application File Path

As mentioned earlier, the "Application Sandbox Directory" is divided into two categories: the application file directory and the system file directory.

The visibility scope of the system file directory to applications is predefined by the OpenHarmony system, and developers need not concern themselves with it.

Here, we focus on the application file directory, as shown in the diagram below. The path of a file or specific directory under the application file directory is called the application file path. Each file path under the application file directory has distinct attributes and characteristics.

![Application file directory structure](figures/application-file-directory-structure.png)

> **Note:**
>
> - Avoid directly using path strings composed of directory names above the fourth-level directory in the diagram, as this may lead to compatibility issues in future application versions due to changes in application file paths.
> - Application file paths, including but not limited to those highlighted in green in the diagram, should be obtained via the `Context` property. For details on obtaining the `Context` and the aforementioned application file paths, refer to the relevant documentation.

1. **First-level directory `data/`**: Represents the application file directory.

2. **Second-level directory `storage/`**: Represents the persistent file directory for the application.

3. **Third-level directories `el1/~el5/`**: Represent different file encryption levels.

    **EL1 (Encryption Level 1)**:
     - Provides basic security for all files on the device. Files protected by EL1 can be accessed without user authentication after the device boots. Unless necessary, this method is not recommended.
     - If ciphertext is directly stolen from the device storage medium, attackers cannot decrypt it offline.

    **EL2 (Encryption Level 2)**:
     - Builds on EL1 by adding file protection after the first authentication. After the device boots, files protected by EL2 can only be accessed after the user completes the first authentication. These files remain accessible until the device is shut down. This is the recommended default method for applications.
     - If the device is lost after shutdown, attackers cannot read files protected by EL2.

    **EL3 (Encryption Level 3)**:
     - Similar to EL4 in overall capability but differs in that new files can be created while the screen is locked but cannot be read. Unless necessary, this method is not required.

    **EL4 (Encryption Level 4)**:
     - Builds on EL2 by adding file protection when the device is locked. Files protected by EL4 cannot be accessed while the screen is locked. Unless necessary, this method is not required.
     - If the device is stolen while locked, attackers cannot read files protected by EL4.

    **EL5 (Encryption Level 5)**:
     - Builds on EL2 by adding file protection when the device is locked. After the screen is locked, files protected by EL5 become inaccessible under certain conditions, but new files can still be created and modified. Unless necessary, this method is not required.
     - By default, EL5-related directories are not generated. Access to EL5-encrypted databases requires specific permissions. For details, refer to [Usage of EL5-Encrypted Databases](../database/cj-data-reliability-security-overview.md).

   > **Note:**
   >
   > Unless otherwise required, applications should store data in the `el2` encrypted directory to maximize data security. However, for certain scenarios (e.g., clock, alarm, wallpaper), files must be accessible before the user's first authentication. In such cases, these files should be stored in the device-level encrypted area (`el1`).
   >
   > Developers can monitor the [COMMON_EVENT_USER_UNLOCKED](../reference/BasicServicesKit/cj-apis-common_event_manager.md#static-const-common_event_user_unlocked) event to detect when the user completes the first authentication.

4. **Fourth- and fifth-level directories**:
    - The `ApplicationContext` can retrieve the application file paths for the `distributedfiles` directory or subdirectories under `base` (e.g., `files`, `cache`, `preferences`, `temp`). Application-wide information can be stored in these directories.
    - The `AbilityContext`, `AbilityStageContext`, and `ExtensionContext` can retrieve HAP-level application file paths. HAP information can be stored in these directories, and files here are deleted when the HAP is uninstalled, without affecting files in the App-level directory. During development, an application may contain one or more HAPs. For details, refer to [Stage Model Application Package Structure](../cj-start/basic-knowledge/application-package-structure-stage.md).

    The following table describes the application file paths and their lifecycles.

   | Directory Name      | Context Property Name | Type               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
   | ------------------- | --------------------- | ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | `bundle`            | `bundleCodeDir`       | Installation Path  | Directory containing the HAP resource packages installed for the App; cleaned upon uninstallation.<br>Do not construct paths to access resource files; use the [Resource Management APIs](../reference/LocalizationKit/cj-apis-resource_manager.md) instead.<br>Can store code resource data, including HAP resource packages, reusable libraries, and plugin resources. Data here can be used for dynamic loading.                                                           |
   | `base`              | N/A                   | Local Device Path  | Directory for persistent data on the local device, with subdirectories like `files/`, `cache/`, `temp/`, and `haps/`; cleaned upon uninstallation.                                                                                                                                                                                                                                                                                                                         |
   | `database`          | `databaseDir`         | Database Path      | Directory for files managed by the distributed database service under `el2` encryption; cleaned upon uninstallation.<br>Only for storing private database data, such as database files. Suitable for distributed database-related files.                                                                                                                                                                                                                                   |
   | `distributedfiles`  | `distributedFilesDir` | Distributed Path   | Directory for distributed files under `el2` encryption; files here can be accessed across devices directly; cleaned upon uninstallation.<br>For data shared across devices, including multi-device backup and collaboration files. Suitable for multi-device scenarios.                                                                                                                                                                                                     |
   | `files`             | `filesDirectory`      | General File Path  | Default long-term storage path for files in internal storage; cleaned upon uninstallation.<br>For any private data, including persistent files, images, media, and logs. Ensures data remains private, secure, and persistent.                                                                                                                                                                                                                                            |
   | `cache`             | `cacheDir`            | Cache Path        | Path for cached or regeneratable files in internal storage; automatically cleaned when quota is exceeded or system space is low. Users may also trigger cleanup via system storage management apps. Applications should verify file existence before re-caching; cleaned upon uninstallation.<br>For offline data, image caches, database backups, and temporary files. Data here may be auto-cleared; avoid storing critical data.                                         |
   | `preferences`       | `preferencesDir`      | Preferences Path  | Directory for configuration or preference data stored via database APIs in internal storage; cleaned upon uninstallation. See [Data Persistence via Preferences](../database/cj-data-persistence-by-preferences.md).<br>For small-scale data like preference and configuration files.                                                                                                                                                                                      |
   | `temp`              | `tempDir`             | Temporary Path    | Directory for files generated and needed only during application runtime; cleaned after exit.<br>For temporary data like database caches, image caches, logs, and downloaded installation packages. Data here can be deleted after use.                                                                                                                                                                                                                                  |

## Correspondence Between Application Sandbox Path and Actual Physical Path

When reading or writing files in the application sandbox path, the operations are mapped to the actual physical paths. The correspondence between sandbox paths and physical paths is shown in the table below.

Here, `<USERID>` represents the current user ID (starting from 100 and incrementing), and `<EXTENSIONPATH>` represents `moduleName-extensionName`.

| Application Sandbox Path          | Physical Path                                                                                                                                                                                                 |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `/data/storage/el1/bundle`           | Application installation directory:<br> `/data/app/el1/bundle/public/<PACKAGENAME>`                                                                                                                          |
| `/data/storage/el1/base`             | Application `el1`-encrypted data directory:<br> - Non-independent sandbox applications: `/data/app/el1/<USERID>/base/<PACKAGENAME>`<br> - Independent sandbox Extension applications: `/data/app/el1/<USERID>/base/+extension-<EXTENSIONPATH>+<PACKAGENAME>`                  |
| `/data/storage/el2/base`             | Application `el2`-encrypted data directory:<br> - Non-independent sandbox applications: `/data/app/el2/<USERID>/base/<PACKAGENAME>`<br> - Independent sandbox Extension applications: `/data/app/el2/<USERID>/base/+extension-<EXTENSIONPATH>+<PACKAGENAME>`              |
| `/data/storage/el1/database`         | Application `el1`-encrypted database directory:<br> - Non-independent sandbox applications: `/data/app/el1/<USERID>/database/<PACKAGENAME>`<br> - Independent sandbox Extension applications: `/data/app/el1/<USERID>/database/+extension-<EXTENSIONPATH>+<PACKAGENAME>` |
| `/data/storage/el2/database`         | Application `el2`-encrypted database directory:<br> - Non-independent sandbox applications: `/data/app/el2/<USERID>/database/<PACKAGENAME>`<br> - Independent sandbox Extension applications: `/data/app/el2/<USERID>/database/+extension-<EXTENSIONPATH>+<PACKAGENAME>` |
| `/data/storage/el2/distributedfiles` | `/mnt/hmdfs/<USERID>/account/merge_view/data/<PACKAGENAME>`                                                                                                                                                  |