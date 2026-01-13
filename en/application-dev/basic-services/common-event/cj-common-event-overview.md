# Common Event Service Overview

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

CES (Common Event Service) provides applications with the capability to subscribe to, publish, and unsubscribe from common events.

## Classification of Common Events

From a system perspective, common events can be categorized into: system common events and custom common events.

- **System Common Events**: Common events defined internally by CES. Currently, only system applications and system services can publish these events, such as HAP installation, update, uninstallation, etc. For the list of currently supported system common events, refer to [System Common Event List](../../reference/BasicServicesKit/cj-apis-common_event_manager.md#struct-support).
- **Custom Common Events**: Events defined by applications, which can be used to implement cross-process event communication capabilities.

Common events can also be classified by their delivery method: unordered common events, ordered common events, and sticky common events.

- **Unordered Common Events**: When CES forwards these events, it does not consider whether subscribers have received them, nor does it guarantee that the order in which subscribers receive the events matches their subscription order.
- **Ordered Common Events**: When CES forwards these events, it prioritizes sending them to subscribers with higher priority levels based on their configured priority. Only after the higher-priority subscribers successfully receive the event will it be sent to lower-priority subscribers. If multiple subscribers share the same priority, they will receive the event randomly.
- **Sticky Common Events**: These allow subscribers to receive events that were published before they subscribed. Unlike regular common events, which can only be received if published after subscription, sticky events can be published before subscription. However, only system applications or system services can publish sticky events. Once published, sticky events persist in the system, and the publisher must request the `ohos.permission.COMMONEVENT_STICKY` permission. For configuration details, refer to [Declaring Permissions](../../security/AccessToken/cj-declare-permissions.md).

## Operational Mechanism

Each application can subscribe to common events as needed. Upon successful subscription, the system will deliver the published events to the corresponding application. These events may originate from the system, other applications, or the application itself.

**Figure 1** Common Event Diagram

![common-event](figures/common-event.png)

## Security Considerations

- **Common Event Publishers**: Without restrictions, any application can subscribe to and read information from common events. Therefore, sensitive information should not be included in common events. The following methods can limit the scope of event recipients:
    - Use the `subscriberPermissions` parameter in [CommonEventPublishData](../../reference/BasicServicesKit/cj-apis-common_event_manager.md#struct-commoneventpublishdata) to specify required permissions for subscribers.
    - Use the `bundleName` parameter in [CommonEventPublishData](../../reference/BasicServicesKit/cj-apis-common_event_manager.md#struct-commoneventpublishdata) to specify the package name of subscribers.
- **Common Event Subscribers**: After subscribing to custom common events, any application can potentially send malicious events to the subscriber. The following methods can limit the scope of event publishers:
    - Use the `publisherPermission` parameter in [CommonEventSubscribeInfo](../../reference/BasicServicesKit/cj-apis-common_event_manager.md#class-commoneventsubscribeinfo) to specify required permissions for publishers.
    - Use the `publisherBundleName` parameter in [CommonEventSubscribeInfo](../../reference/BasicServicesKit/cj-apis-common_event_manager.md#class-commoneventsubscribeinfo) to specify the package name of publishers.
- Custom common event names must be globally unique to avoid conflicts with other events.