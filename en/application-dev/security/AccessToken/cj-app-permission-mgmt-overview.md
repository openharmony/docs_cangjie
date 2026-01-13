# Overview of Application Permission Control  

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

## Introduction  

The system provides a universal permission access mechanism that allows applications to access system resources (e.g., contacts) and system capabilities (e.g., camera, microphone) while protecting system data (including user personal data) or functionalities from improper or malicious use.  

Application permissions can be categorized into two protection targets: data and functionality:  

- **Data** includes personal data (e.g., photos, contacts, calendar, location) and device data (e.g., device identifiers, camera, microphone).  
- **Functionality** includes device capabilities (e.g., accessing the camera/microphone, making phone calls, connecting to the internet) and application features (e.g., displaying floating windows, creating shortcuts).  

## Basic Principles of Permission Usage  

Reasonable usage scenarios facilitate proper permission requests and usage. When developing applications, permission requests must adhere to the following principles:  

- **Permissions required by the application (including third-party libraries referenced by the application)** must be explicitly declared in the application's configuration file, strictly following the permission development guidelines. Refer to [Declaring Permissions](./cj-declare-permissions.md).  
- **Permission requests must follow the principle of minimal necessity.** Avoid requesting unnecessary or deprecated permissions. Excessive permission requests may raise user concerns about application security and degrade the user experience, potentially affecting installation and retention rates.  
- **When requesting sensitive permissions**, the application must provide a justification for usage. Sensitive permissions typically involve user privacy, such as location, camera, microphone, calendar, fitness data, body sensors, music, files, photos, and videos. Refer to [Requesting User Authorization](./cj-request-user-authorization.md).  
- **Sensitive permissions must be dynamically requested before executing the corresponding business functionality**, ensuring compliance with privacy minimization requirements.  
- **If a user denies a permission**, unrelated business functionalities of the application should remain fully operational.  

## Authorization Methods  

Based on the authorization method, permissions can be classified into `system_grant` (system authorization) and `user_grant` (user authorization).  

### system_grant (System Authorization)  

`system_grant` refers to permissions granted by the system. Under this type of authorization, the data accessed by the application does not involve sensitive user or device information, and the operations performed have a controllable impact on the system or other applications.  

If an application requests a `system_grant` permission, the system automatically grants the permission during installation.  

### user_grant (User Authorization)  

`user_grant` refers to permissions granted by the user. Under this type of authorization, the data accessed by the application may involve sensitive user or device information, and the operations performed could significantly impact the system or other applications.  

For such permissions, the application must not only declare them in the installation package but also dynamically request user authorization at runtime via a pop-up dialog. The application obtains the permission only after the user manually grants it, enabling access to the target operation.  

For example, in the [Application Permission List](./cj-permissions-for-all.md), permissions for the microphone and camera fall under `user_grant`, with detailed usage justifications provided. Applications must display the requested `user_grant` permissions on their app store detail pages.  

## Permission Groups and Sub-Permissions  

To minimize the number of permission pop-ups and optimize the user experience, the system groups logically related `user_grant` permissions into permission groups.  

When an application requests permissions, all permissions within the same group are presented in a single pop-up for user authorization. Each permission within a group is referred to as a sub-permission.  

The grouping of permissions is not fixed; a permission's group affiliation may change. For the current list of supported permission groups, refer to [Application Permission Group List](./cj-app-permission-group-list.md).  

## Key Concepts in the Permission Mechanism  

- **TokenID**  

  The system uses **TokenID** (Token identity) as the unique identifier for an application. The permission management service manages the application's **AT (Access Token)** information based on the TokenID, including the application identity (APP ID), sub-user ID, application clone index, application APL, and permission authorization status. During resource access, the system maps the TokenID to the corresponding application's permission status for authentication, thereby controlling the application's resource access behavior.  

  Notably, the system supports multi-user and application cloning features. The same application under different sub-users or clones will have distinct ATs, each with a unique TokenID.  

- **APL Level**  

  To prevent excessive or abusive permission requests, the system configures different permission scopes based on the **APL (Ability Privilege Level)**.  

  APL defines the priority level of an application's permission requests. Applications with different APL levels can request permissions of corresponding levels.  

- **Application APL Levels**  

  Applications are classified into the following three levels, in ascending order:  

  | APL Level      | Description                                                                 |
  | :------------- | :-------------------------------------------------------------------------- |
  | `normal`       | By default, applications are assigned the `normal` APL level.               |
  | `system_basic` | Applications at this level provide fundamental system services.             |
  | `system_core`  | Applications at this level provide core operating system capabilities.<br/>**Note:** Applications cannot be configured as `system_core`. |  

- **Permission APL Levels**  

  Permissions are categorized into three levels based on their openness to different application levels, in ascending order:  

  | APL Level      | Description                                                                 | Open Scope                                                                 |
  | :------------- | :-------------------------------------------------------------------------- | :------------------------------------------------------------------------- |
  | `normal`       | Allows applications to access ordinary system resources beyond default rules, such as configuring Wi-Fi or using the camera.<br/>These resources pose minimal risk to user privacy or other applications. | Applications with APL level `normal` or higher.                            |
  | `system_basic` | Allows access to resources related to basic system services (e.g., system settings, authentication).<br/>These resources pose higher risks to user privacy and other applications. | - Applications with APL level `system_basic` or higher.<br/>- Some permissions are **restricted-open** to `normal`-level applications. Refer to [Restricted-Open Permissions](./cj-declare-permissions-in-acl.md). |
  | `system_core`  | Involves access to core operating system resources. Damage to these resources may render the OS inoperable. | - Applications with APL level `system_core`.<br/>- Open only to system applications. |  

- **Access Control List (ACL)**  

  As described above, permission APL levels and application APL levels are strictly correlated. By default, applications with lower APL levels cannot request higher-level permissions. The **ACL (Access Control List)** provides a special channel for low-level applications to request high-level permissions.  

  Each system permission defines an **"ACL-enabled"** field. If this field is `TRUE`, the application can use ACL to request the permission across levels. For specific permission definitions, refer to [Restricted-Open Permissions](./cj-declare-permissions-in-acl.md).  

  **Example Scenario:** Suppose a developer is working on Application A with APL level `normal`. Due to functional requirements, A needs to request Permission P, which has APL level `system_basic`. If P's ACL-enabled field is `TRUE`, A can request P via ACL despite the level mismatch.