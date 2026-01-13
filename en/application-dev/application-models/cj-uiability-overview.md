# UIAbility Component Overview

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

## Overview

[UIAbility](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) is a UI-containing application component primarily designed for user interaction.

UIAbility design philosophy:

1. Supports cross-device migration and multi-device collaboration at the application component level.

2. Supports multiple device types and window forms.

UIAbility division principles and recommendations:

The UIAbility component serves as the basic unit for system scheduling, providing applications with windows for interface rendering. An application may contain one or multiple UIAbility components. For example, in a payment application, the entry function and payment/receipt function can be configured as separate UIAbility components.

Each UIAbility component instance will display a corresponding task in the recent tasks list.

For developers, the choice between single or multiple UIAbility components should be based on specific scenarios. Division recommendations are as follows:

- If developers want to see a single task in the task view, it's recommended to adopt the "one UIAbility + multiple pages" approach to avoid unnecessary resource loading.
- If developers want to see multiple tasks in the task view or need to open multiple windows simultaneously, it's recommended to use multiple UIAbility components to implement different functions.

    For example, in instant messaging applications, developing the message list and audio/video call functions as separate UIAbility components not only facilitates task window switching but also enables split-screen display of two application task windows on a single screen.

> **Note:**
>
> The task view is used for quickly viewing and managing all currently running tasks or applications on the device.

## Declaration Configuration

For an application to properly use UIAbility, it's necessary to declare the UIAbility's name, entry point, label, and other relevant information in the [abilities tag](../cj-start/basic-knowledge/module-configuration-file.md#abilities标签) of the [module.json5 configuration file](../cj-start/basic-knowledge/module-configuration-file.md).

```json
{
  "module": {
    // ...
    "abilities": [
      {
        "name": "EntryAbility", // Name of the UIAbility component
        "srcEntry": "ohos_app_cangjie_entry.MainAbility", // Code path of the UIAbility component
        "description": "$string:EntryAbility_desc", // Description of the UIAbility component
        "icon": "$media:startIcon", // Icon of the UIAbility component
        "label": "$string:EntryAbility_label", // Label of the UIAbility component
        "startWindowIcon": "$media:startIcon", // Resource file index for the UIAbility component's startup page icon
        "startWindowBackground": "$color:start_window_background", // Resource file index for the UIAbility component's startup page background color
        // ...
      }
    ]
  }
}
```

Additionally, registration must be completed.

<!-- compile -->

```cangjie
import kit.AbilityKit.UIAbility

let ENTRYABILITY_REGISTER_RESULT = UIAbility.registerCreator("EntryAbility", {=> MainAbility()})
```