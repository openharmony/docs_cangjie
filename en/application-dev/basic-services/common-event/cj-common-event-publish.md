# Public Event Publishing

## Scenario Description

When needing to publish a custom public event, you can use the [publish()](../../reference/BasicServicesKit/cj-apis-common_event_manager.md#static-func-publishstring) method to publish the event. Published public events can carry data for subscribers to parse and process further.

> **Note:**
>
> Sticky public events that have already been sent can still be received by later subscribers. Other public events require subscription before reception. For subscription details, refer to the [Public Event Subscription Section](./cj-common-event-subscription.md).

## Interface Description

For detailed interface information, please refer to the [Interface Documentation](../../reference/BasicServicesKit/cj-apis-common_event_manager.md#static-func-publishstring).

| Interface Name                                               | Description                  |
| ------------------------------------------------------------ | ---------------------------- |
| publish(event:&nbsp;String): Unit | Publish a public event.      |
| publish(event:&nbsp;String,&nbsp;options:&nbsp;[CommonEventPublishData](../../reference/BasicServicesKit/cj-apis-common_event_manager.md#struct-commoneventpublishdata)): Unit | Publish a public event with specified information. |

## Publishing Public Events Without Carrying Information

Public events without carrying information can only publish unordered public events.

1. Import the module.

   <!-- compile -->

   ```cangjie
   import kit.BasicServicesKit.*
   ```

2. Pass the event name to be published and the callback function to publish the event.

   <!-- compile -->

   ```cangjie
   // Publish a public event, where the event field should be replaced with the actual event name.
   let support1 = Support.COMMON_EVENT_SCREEN_ON
   CommonEventManager.publish(support1)
   ```

## Publishing Public Events Carrying Information

Public events carrying information can be published as unordered public events, ordered public events, or sticky events. This can be configured via the isOrdered and isSticky fields in the [CommonEventPublishData](../../reference/BasicServicesKit/cj-apis-common_event_manager.md#struct-commoneventpublishdata) parameter.

1. Import the module.

   <!-- compile -->

   ```cangjie
   import kit.BasicServicesKit.*
   ```

2. Construct the public event information to be published.

   <!-- compile -->

   ```cangjie
   // Public event related information
    let pData = CommonEventPublishData(
      bundleName: "com.example.myapplication", 
      data: "newbee", 
      code: 123321,
      subscriberPermissions: Array<String>(),
      isOrdered: false,
      isSticky: false,
      parameters: HashMap<String, ValueType>()
   )
   ```

3. Pass the event name to be published, the specified information to be published, and the callback function to publish the event.

   <!-- compile -->

   ```cangjie
   // Publish a public event, where the event field should be replaced with the actual event name
   let support1 = Support.COMMON_EVENT_SCREEN_ON
   CommonEventManager.publish(support1, options: pData)
   ```