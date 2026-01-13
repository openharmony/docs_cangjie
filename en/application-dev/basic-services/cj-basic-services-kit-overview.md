# Introduction to Basic Services Kit  

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

The Basic Services Kit serves as a foundational service suite, providing application developers with essential capabilities. Common functionalities such as clipboard read/write, file upload/download, file compression, file printing, inter-process/inter-thread communication, device management, and application account management are all offered by this Kit.  

## Usage Scenarios  

The Basic Services Kit provides developers with various foundational capabilities to meet development needs across different scenarios.  

Typical usage scenarios include:  

- **Clipboard Read/Write**:  
    - Local copy-paste: For example, copying text in Application A and pasting it into other applications.  
    - Cross-device copy-paste: For example, copying text in Device A's browser and pasting it into Device B's notes app.  

- **File Upload/Download**:  
    - Small file foreground upload/download: Posting social media updates (images, short videos, etc.), sending files to friends, or saving images locally—typically involving small data volumes that require immediate user feedback.  
    - Large file background upload/download: Cloud storage synchronization, movie downloads—typically involving large data volumes that can be executed in the background with support for resumable transfers.  

- **Inter-Process/Inter-Thread Communication**:  
    - Inter-process communication: For example, an ExtensionAbility sending events to the main process.  
    - Inter-thread communication: For example, a worker thread passing processed network request events back to the UI main thread.  

## Capability Scope  

Categorized by different usage scenarios, this Kit primarily includes the following capabilities:  

- **Data File Handling**:  
    - [Compression](../reference/AbilityKit/cj-apis-bundle_manager.md): Provides file compression and decompression capabilities.  
    - [Upload/Download](../reference/BasicServicesKit/cj-apis-request-agent.md): Provides foundational capabilities for file upload/download and background transfer agents.  

- **Inter-Process/Inter-Thread Communication**:  
    - [Common Event](../reference/BasicServicesKit/cj-apis-common_event_manager.md): Enables inter-process communication, including subscribing to, publishing, and unsubscribing from common events. For related development guidelines, refer to [Common Event Introduction](./common-event/cj-common-event-overview.md).  

- **Device Management**:  
    - [Device Information](../reference/BasicServicesKit/cj-apis-device_info.md): Provides the ability to query product information, such as device type, brand name, product series, and version number.  
    - [Settings Data Items](../reference/BasicServicesKit/cj-apis-settings.md): Enables querying system settings data items, such as whether airplane mode or touch browsing is enabled.  
    - [Battery Information Query](../reference/BasicServicesKit/cj-apis-battery_info.md): Provides the ability to query battery information.  

- **Others**:  
    - [Time and Timezone](../reference/BasicServicesKit/cj-apis-system_date_time.md): Provides the ability to retrieve system time and timezone.  

## Relationship with Other Kits  

- **[Ability Kit](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md)**: Inter-process communication in the Ability Kit requires the use of common events from this Kit.  

- **[Core File Kit](../reference/CoreFileKit/cj-apis-file_fs.md)**: Unlike the Core File Kit, which primarily provides file access and management capabilities for scenarios such as application file sharing and data backup/recovery, this Kit is used for development scenarios involving file compression, upload/download, and printing.