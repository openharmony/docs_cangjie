# Subscribing to Application Events (Cangjie)

HiAppEvent provides event subscription interfaces for locally retrieving application events.

## Interface Description

For detailed usage instructions of the API interfaces (parameter usage restrictions, specific value ranges, etc.), please refer to the [Application Event Logging API Documentation](../reference/PerformanceAnalysisKit/cj-apis-hiappevent.md).

**Event Logging Interface Functions:**

| Interface Name                  | Description                |
| ------------------------------- | -------------------------- |
| write(info: AppEventInfo): Unit | Application event logging method. |

**Subscription Interface Functions:**

| Interface Name                                                   | Description                                          |
| ---------------------------------------------------------------- | --------------------------------------------------- |
| addWatcher(watcher: Watcher): Option\<AppEventPackageHolder>     | Adds an application event watcher to subscribe to application events. |
| removeWatcher(watcher: Watcher): Unit                            | Removes an application event watcher to unsubscribe from application events. |

## Development Steps

Taking the implementation of event logging and subscription for user button click behavior as an example, the development steps are described below.

1. Create a new Cangjie application project and edit the "entry > src > main > cangjie > main_ability.cj" file in the project to import the dependency modules:

    <!-- compile -->

    ```cangjie
    import kit.PerformanceAnalysisKit.*
    import kit.PerformanceAnalysisKit.{Watcher as hiWatcher}
    import ohos.base.*
    ```

2. Edit the "entry > src > main > cangjie > main_ability.cj" file in the project and add a subscription to user button click events in the onCreate function. The sample code is as follows:

    <!-- compile -->

    ```cangjie
    var condition = TriggerCondition(row: 1, size: 120, timeOut: 0)
    var appEventFilter = [AppEventFilter("cangjie_watcher")]
    var watcher = hiWatcher(
        "watcher1",
        triggerCondition: condition,
        appEventFilters: appEventFilter,
        onTrigger: Some(
            {
                row, size, holder =>
                Hilog.info(0, "test_hiAppEvent_addWatcher_01",
                    "HiAppEvent onTrigger: curRow=${row},curSize=${size}")
                while (let Some(v) <- holder.takeNext()) {
                    let eventPkg = v
                    Hilog.info(0, "test_hiAppEvent_addWatcher_01", "HiAppEvent packageId=${eventPkg.packageId}")
                    Hilog.info(0, "test_hiAppEvent_addWatcher_01", "HiAppEvent row=${eventPkg.row}")
                    Hilog.info(0, "test_hiAppEvent_addWatcher_01", "HiAppEvent size=${eventPkg.size}")
                    for (i in 0..eventPkg.data.size) {
                        Hilog.info(0, "test_hiAppEvent_addWatcher_01", "HiAppEvent info=${eventPkg.data[i]}")
                    }
                }
            }
        )
    )
    ```

3. Edit the "entry > src > main > cangjie > index.cj" file in the project to import the dependency modules:

    <!-- compile -->

    ```cangjie
    import kit.PerformanceAnalysisKit.*
    import kit.PerformanceAnalysisKit.{Watcher as hiWatcher}
    import ohos.base.*
    ```

4. Edit the "entry > src > main > cangjie > index.cj" file in the project and add a button to perform event logging in its onClick function to record button click events. The sample code is as follows:

    <!-- compile -->

    ```cangjie
    Button("writeTest").onClick({ evt =>
        // Perform event logging in the button click function to record button click events
        let eventParams = HashMap<String, EventValueType>([("click_time", IntValue(100))])
        let eventInfo: AppEventInfo = AppEventInfo(
            // Event domain definition
            "button",
            // Event name definition
            "click",
            // Event type definition
            EventType.Behavior,
            // Event parameter definition
            eventParams)

        HiAppEvent.write(eventInfo)
    })
    ```

5. Click the Run button in the DevEco Studio interface to run the application project. Then click the "writeTest" button on the application interface to trigger a button click event logging.

6. You can view the logs of successful button click event logging and the processed logging event data after triggering the subscription callback in the Log window:

   ```text
   HiAppEvent success to write event
   HiAppEvent eventPkg.packageId=0
   HiAppEvent eventPkg.row=1
   HiAppEvent eventPkg.size=124
   HiAppEvent eventPkg.info={"domain_":"button","name_":"click","type_":4,"time_":1670268234523,"tz_":"+0800","pid_":3295,"tid_":3309,"click_time":100}
   ```