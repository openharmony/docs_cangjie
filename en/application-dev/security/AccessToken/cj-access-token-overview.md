# Access Control Overview

By default, applications can only access limited system resources. However, in certain scenarios, applications may require extended functionalities that necessitate access to additional system data (including user personal data) and capabilities. The system must also provide explicit interfaces to share its data or functionalities externally.

The system employs access control mechanisms to prevent improper or malicious use of data or functionalities. Current access control mechanisms involve multiple aspects, including application sandboxing, application permissions, system controls, and other solutions.

## Application Sandbox

Applications running on the system are deployed within protected sandboxes. Through the security isolation mechanisms of sandboxes, improper application behaviors (such as unauthorized data access between applications or device tampering) can be restricted. Each application is assigned a unique ID ([TokenID](./cj-app-permission-mgmt-overview.md#basic-concepts-in-permission-mechanisms)), which the system uses to identify and limit the application's access behaviors.

The application sandbox ensures that only the intended audience can access the data within an application and restricts the scope of data that the application can access.

## Application Permissions

The system sets process domains and data domain labels based on the Application Privilege Level (APL) of applications. Through access control mechanisms, it restricts the range of data that applications can access, thereby systematically reducing the risk of data leakage.

Applications with different APL levels can request different permission levels. Various system resources (e.g., contacts) or system capabilities (e.g., accessing the camera or microphone) are protected by different application permissions. Strict hierarchical permission protection effectively mitigates malicious attacks, ensuring system security and reliability.

For detailed information on application permission management, refer to [Application Permission Management Overview](./cj-app-permission-mgmt-overview.md).