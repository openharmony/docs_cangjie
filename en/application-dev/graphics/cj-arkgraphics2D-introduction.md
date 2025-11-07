# Introduction to ArkGraphics 2D

ArkGraphics 2D (Ark 2D Graphics Service) primarily provides capabilities related to graphics rendering and display. Developers can build applications based on a unified set of graphics APIs, making application development simpler and more efficient.

## Capability Scope

- Provides the ability to specify frame rates for different types of content, which can be used for developer self-rendered content. For details, refer to [Variable Frame Rate Introduction](./cj-displaysync-overview.md).

## Usage Scenarios

Custom frame rate scenarios: Supports developers in customizing frame rates for rendering based on different content and needs. For example, setting different frame rates for different game scenes and interfaces to enhance user experience smoothness while achieving balanced power consumption.

## Key Features

- Multiple frame rates within the same window: Supports customizing different rendering frame rates for different content within the same window, such as animations or self-rendered UI, with independent operation between different content.

- Dynamic frame rate configuration for balancing experience and power consumption: Supports third-party frameworks in dynamically requesting rendering frame rates based on UI scenarios, such as gaming and video services, to balance smooth experience and power efficiency.