# Application Permissions List

The method for requesting permissions varies depending on their scope of availability and authorization method.

The system currently maintains the following permissions list. Developers can search based on actual requirements and determine the appropriate method for requesting corresponding permissions.

- [Open Permissions (System Authorization)](./cj-permissions-for-all.md)

    All applications may request these permissions. After an application requests such permissions, the system will automatically grant them during installation.

- [Open Permissions (User Authorization)](./cj-permissions-for-all-user.md)

    All applications may request these permissions. After requesting such permissions, applications must additionally obtain user authorization through pop-up prompts during runtime.

- [Permissions Available for Enterprise Applications](./cj-permissions-for-enterprise-apps.md)

    Only available for enterprise normal applications and MDM applications. Applications with distribution types (app-distribution-type) as enterprise_normal (enterprise normal applications) or enterprise_mdm (MDM applications) may request these. Applications must confirm the authorization method and request accordingly.

- [Permissions Available for MDM Applications](./cj-permissions-for-mdm-apps.md)

    Only MDM applications may request these permissions. Applications must confirm the authorization method and request accordingly.