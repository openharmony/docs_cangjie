# Dynamic Subscription to Public Events

## Scenario Description

Dynamic subscription refers to an application subscribing to a public event while it is running. During operation, if a subscribed event is published, the application that subscribed to that event will receive the event along with its transmitted parameters.

For example, if an application wishes to receive low battery level events during its operation and reduce its power consumption based on these events, it can dynamically subscribe to low battery events. Upon receiving such an event, the application can shut down non-essential tasks to conserve power.

Subscribing to certain system public events requires first [applying for permissions](../../security/AccessToken/cj-determine-application-mode.md).

> **Note:**
>
> The lifecycle of the subscriber object must be managed by the integrator. It should be actively destroyed and released when no longer in use to prevent memory leaks.

## Interface Description

For detailed interfaces, refer to the [Interface Documentation](../../reference/BasicServicesKit/cj-apis-common_event_manager.md).

| Interface Name | Description |
| -------- | -------- |
| createSubscriber(subscribeInfo:&nbsp;[CommonEventSubscribeInfo](../../reference/BasicServicesKit/cj-apis-common_event_manager.md#class-commoneventsubscribeinfo)): [CommonEventSubscriber](../../reference/BasicServicesKit/cj-apis-common_event_manager.md#class-commoneventsubscriber)| Creates a subscriber object. |
| subscribe(subscriber:&nbsp;[CommonEventSubscriber](../../reference/BasicServicesKit/cj-apis-common_event_manager.md#class-commoneventsubscriber),&nbsp;callback: ([CommonEventData](../../reference/BasicServicesKit/cj-apis-common_event_manager.md#struct-commoneventdata)) -> Unit): Unit | Subscribes to a public event. |

## Development Steps

1. Import the module.

   <!-- compile -->

   ```cangjie
   import kit.BasicServicesKit.*
   ```

2. Create subscriber information. For detailed data types and parameters of subscriber information, refer to the [CommonEventSubscribeInfo](../../reference/BasicServicesKit/cj-apis-common_event_manager.md#class-commoneventsubscribeinfo) documentation.

   <!-- compile -->

   ```cangjie
   // Used to store the successfully created subscriber object for subsequent subscription and unsubscription actions
   let subscriber: CommonEventSubscriber
   // Subscriber information; the event field should be replaced with the actual event name
   let support1 = Support.COMMON_EVENT_SCREEN_ON
   let events = [support1]
   let subscribeInfo = CommonEventSubscribeInfo(events)
   ```

3. Create a subscriber and store the returned subscriber object `subscriber` for performing subsequent operations such as subscription, unsubscription, and receiving event callbacks.

   <!-- compile -->

   ```cangjie
   // Create subscriber callback
   subscriber = CommonEventManager.createSubscriber(subscribeInfo)
   ```

4. Create a subscription callback function, which will be triggered when an event is received. The `data` returned by the callback function contains the public event name, data carried by the publisher, and other information. For detailed parameters and data types of public event data, refer to the [CommonEventData](../../reference/BasicServicesKit/cj-apis-common_event_manager.md#struct-commoneventdata) documentation.

   <!-- compile -->

   ```cangjie
      // Public event subscription callback
   let callback = {
      a: ?BusinessException, b: ?CommonEventData =>
         Hilog.info(0, "TestCEM", "=======================================")
         Hilog.info(0, "TestCEM", "callback excute success!")
   }
   CommonEventManager.subscribe(subscriber, callback)
   ```