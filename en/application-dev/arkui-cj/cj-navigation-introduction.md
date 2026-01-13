# Overview of Component Navigation and Page Routing  

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

Component Navigation (Navigation) and page routing (@ohos.router) both support page navigation within an application. However, Component Navigation offers greater flexibility by enabling navigation within components. It provides enhanced "Write Once, Run Anywhere" (WORA) capabilities, more flexible page stack operations, and supports richer animations and lifecycle management. Therefore, it is recommended to use Component Navigation (Navigation) for page navigation and intra-component navigation to achieve a better user experience.  

## Architectural Differences  

From the perspective of the ArkUI component tree hierarchy, pages managed by Router were originally located under the stage node for page stack management. The Navigation component, as a navigation container, can be mounted under a single page node or be layered and nested. Navigation manages the title bar, content area, and toolbar. The content area displays user-defined page content and supports routing capabilities. This design of Navigation offers the following advantages:  

![navigation_introduction](./figures/navigation_introduction.png)  

1. **Explicit Interface Separation**: Clearly distinguishes the title bar, content area, and toolbar, enabling more flexible management and UX animation capabilities.  

2. **Explicit Routing Container Concept**: Developers can determine the placement of routing containers, supporting display in full-modal, half-modal, or pop-up windows.  

3. **Integrated UX Design and Multi-Device Adaptation**: Provides unified title display, page switching, and single/dual-column adaptation by default.  

4. **Flexible Page Configuration**: Based on the universal [UIBuilder](./paradigm/cj-macro-builder.md) capability, developers can define the mapping between page aliases and UI, offering more flexible page configuration.  

5. **Rich Transition Animations**: Converts page transition animations into component property animations, leveraging component attribute animations and shared element animations for richer and more flexible effects.  

6. **Open Page Stack Object**: Developers can inherit and better manage page display by extending the page stack object.