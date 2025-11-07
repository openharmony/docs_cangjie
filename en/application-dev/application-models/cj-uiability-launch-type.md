# UIAbility Component Launch Mode

The launch mode of [UIAbility](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) refers to the different presentation states of UIAbility instances during startup. For different business scenarios, the system provides two launch modes:

- [UIAbility Component Launch Mode](#uiability-component-launch-mode)
  - [singleton Launch Mode](#singleton-launch-mode)
  - [multiton Launch Mode](#multiton-launch-mode)

> **Note:**
>
> `standard` was the former name of `multiton`, with the same effect as the multi-instance mode.

## singleton Launch Mode

The singleton launch mode is the single-instance mode, which is also the default launch mode.

Each time the [startAbility()](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#func-startabilitywant-startOptions) method is called, if an instance of this type of [UIAbility](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) already exists in the application process, the system will reuse the existing UIAbility instance. There is only one unique instance of this UIAbility in the system, meaning only one instance of this type of UIAbility appears in the recent tasks list.

**Figure 1** Demonstration of Singleton Mode

<img src="./figures/uiability-launch-type1.gif" style="zoom:90%">

> **Note:**
>
> If the UIAbility instance of the application has already been created and is configured in singleton mode, calling [startAbility()](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#func-startabilitywant-startOptions) again to launch this UIAbility instance will not create a new instance. Instead, it will only trigger the [onNewWant()](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#func-onnewwantwant-launchparam) callback of the existing UIAbility instance, without entering its [onCreate()](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#func-oncreatewant-launchparam) and [onWindowStageCreate()](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#func-onwindowstagecreatewindowstage) lifecycle callbacks. If the existing instance is still in the process of being created, calling the startAbility interface to launch it will result in error code 16000082.

To use the singleton launch mode, configure the `launchType` field as `singleton` in the [module.json5 configuration file](../cj-start/basic-knowledge/module-configuration-file.md).

```json
{
  "module": {
    // ...
    "abilities": [
      {
        "launchType": "singleton",
        // ...
      }
    ]
  }
}
```

## multiton Launch Mode

The multiton launch mode is the multi-instance mode. Each time the [startAbility()](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#func-startabilitywant-startoptions) method is called, a new instance of this type of [UIAbility](../reference/AbilityKit/cj-apis-app-ability-ui_ability.md#class-uiability) is created in the application process. This means multiple instances of this type of UIAbility can be seen in the recent tasks list. In this case, the UIAbility can be configured as multiton (multi-instance mode).

**Figure 2** Demonstration of Multiton Mode

<img src="./figures/uiability-launch-type2.gif" style="zoom:90%">

To develop using the multiton launch mode, configure the `launchType` field as `multiton` in the [module.json5 configuration file](../cj-start/basic-knowledge/module-configuration-file.md).

```json
{
  "module": {
    // ...
    "abilities": [
      {
        "launchType": "multiton",
        // ...
      }
    ]
  }
}
```