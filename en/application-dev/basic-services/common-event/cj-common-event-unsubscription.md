# Unsubscribe from Dynamic Common Events

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

## Scenario Description

After completing business requirements, dynamic subscribers should proactively unsubscribe. Call the [unsubscribe()](../../reference/BasicServicesKit/cj-apis-common_event_manager.md#static-func-unsubscribecommoneventsubscriber) method to cancel event subscriptions.

## Interface Description

| Interface Name | Description |
| -------- | -------- |
| unsubscribe(subscriber:&nbsp;[CommonEventSubscriber](../../reference/BasicServicesKit/cj-apis-common_event_manager.md#class-commoneventsubscriber)): Unit | Unsubscribes from common events. |

## Development Steps

1. Import the module.

   <!-- compile -->

   ```cangjie
   import kit.BasicServicesKit.*
   ```

2. Follow the steps in the [Dynamic Common Event Subscription](./cj-common-event-subscription.md) section to subscribe to an event.

3. Call the [unsubscribe()](../../reference/BasicServicesKit/cj-apis-common_event_manager.md#static-func-unsubscribecommoneventsubscriber) method in CommonEvent to unsubscribe from an event.

   <!-- compile -->

   ```cangjie
   // subscriber is the subscriber object created during event subscription
    CommonEventManager.unsubscribe(subscriber)
   ```