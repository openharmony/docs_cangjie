# Development Preparation

This document is intended for beginners in Cangjie application development. By building a simple application with page navigation/return functionality (as shown in the figure below), you can quickly understand the main files in the project directory and familiarize yourself with the Cangjie application development process.

![cangjieFirstDemo](../../figures/cangjieFirstDemo.png)

Before getting started, you need to understand two fundamental concepts about Cangjie applications: the UI framework and the application model.

## Basic Concepts

### UI Framework

Cangjie provides a UI development framework that offers developers essential capabilities for application UI development, such as various components, layout calculations, UI interactions, rendering, and more.

### Application Model

The application model is an abstraction provided by OpenHarmony, offering developers the necessary capabilities for application development. It includes essential components and runtime mechanisms. With the application model, developers can build applications based on a unified framework, making development simpler and more efficient.

Cangjie applications use the Stage model. In this model, classes like `AbilityStage` and `WindowStage` serve as the "stage" for application components and window management, hence the name Stage model.

The Quick Start guide provides multiple development examples with different types of pages, all built on the Stage model to help developers understand the above concepts and the application development process.

- [Build Your First Cangjie Application](./cj-quick-start-first-cangjie-app.md#build-your-first-cangjie-application): Create a simple pure Cangjie application with page navigation/return functionality.
- [Build Your First Cangjie and ArkTS Hybrid Application](./cj-quick-start-first-cangjie-hybrid-app.md#build-your-first-cangjie-and-arkts-hybrid-application): Develop a simple hybrid application with Cangjie and ArkTS, featuring page navigation/return functionality.
- [Incrementally Adopt Cangjie in an Existing ArkTS Project](./cj-quick-start-first-cangjie-hybrid-module.md#incrementally-adopt-cangjie-in-an-existing-arkts-project): Based on a simple pure ArkTS application with page navigation/return functionality, introduce Cangjie to develop incremental features.
- [Calling ArkTS Third-Party Modules from Cangjie](./cj-quick-start-dts2cj-plugin-usage.md#calling-arkts-third-party-modules-from-cangjie): Invoke functionalities of ArkTS third-party libraries in Cangjie code.

After understanding these basic concepts, proceed to the next step by referring to [Build Your First Cangjie Application](cj-quick-start-first-cangjie-app.md#build-your-first-cangjie-application) for hands-on experience and learning.