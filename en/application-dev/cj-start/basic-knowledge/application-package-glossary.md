# Application Package Terminology

## E

### ExtensionAbility

A component type name in the Stage model, referring to the ExtensionAbility component. It provides extension capabilities for specific scenarios (such as cards, input methods) to meet diverse usage requirements.

## H

### HAP

Harmony Ability Package. A HAP file contains all contents of an application, consisting of code, resources, third-party libraries, and application configuration files. The file extension is .hap.

### HAR

Harmony Archive, a static shared package for compile-time reuse. It may contain code, C++ libraries, resources, and configuration files. The file extension is .har, used for sharing code and resources.

### HSP

Harmony Shared Package, a dynamic shared package for runtime reuse. It may contain code, C++ libraries, resources, and configuration files. The file extension is .hsp, used for sharing code and resources.

## M

### Module

A part of an application where each module has its own module.json5 configuration file. In project engineering, Entry, Feature, HSP, and HAR are all considered application modules.

## S

### Stage Model

An application model introduced since API version 9, providing two major types of application components: UIAbility and ExtensionAbility. As this model also includes classes like AbilityStage and WindowStage that serve as "stages" for application components and Window interfaces, it is named the Stage model.

## U

### UIAbility

A component type name in the Stage model, referring to the UIAbility component. It contains UI elements and provides UI display capabilities, primarily used for user interaction.