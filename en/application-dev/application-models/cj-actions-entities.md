# Common Actions and Entities (Not Recommended)

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

## Actions

Represents generic operations that the caller intends to perform (e.g., view, share, application details). When actions are declared in the [skills field](../cj-start/basic-knowledge/module-configuration-file.md#skills-tag) of the callee application's configuration file, it indicates that the application supports these declared operations. Common actions are listed below.

**Common Actions:**

- ACTION_HOME: The action to launch the application's entry component, which must be used in conjunction with ENTITY_HOME. The system desktop application icon serves as an explicit entry component, and clicking it triggers the action to launch the entry component. Multiple entry components can be configured.
- ACTION_CHOOSE: Selects local resource data, such as contacts or photo albums. The system typically provides corresponding Picker applications for different data types, such as contacts and galleries.
- ACTION_VIEW_DATA: Views data. When a URI is used, it displays the content corresponding to that URI. For specific operational procedures, refer to [Launching File Processing Applications via startAbility](./cj-file-processing-apps-startup.md).
- ACTION_VIEW_MULTIPLE_DATA: Performs the operation of sending multiple data records.

## Entities

Represents category information of the target application component (e.g., browser, video player). When entities are declared in the [skills field](../cj-start/basic-knowledge/module-configuration-file.md#skills-tag) of the callee application's configuration file, it indicates the categories supported by the application. Common entities are listed below.

**Common Entities:**

- ENTITY_DEFAULT: Default category with no actual meaning.
- ENTITY_HOME: Category for the home screen with a clickable icon entry.
- ENTITY_BROWSABLE: Indicates the browser category.