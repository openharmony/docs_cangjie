# Introduction to Ability Kit  

Ability Kit (Program Framework Service) provides the application model for application development and operation, abstracting and refining the capabilities required by applications for developers. It offers essential components and operational mechanisms for applications. With the application model, developers can build applications based on a unified framework, making development simpler and more efficient.  

## Usage Scenarios  

- **Multi-Module Development for Applications**: Applications can implement functionality through different types of modules (HAP, HAR). Among them, HAP is used to realize application features and functionalities, while HAR enables code and resource sharing.  
- **Intra-Application Interaction**: Different components within an application can navigate to each other. For example, in a payment app, the entry UIAbility component can launch the payment/receipt UIAbility component.  
- **Inter-Application Interaction**: The current application can start other applications to complete specific tasks or operations. For instance, launching a browser app to open a website or a file app to browse or edit files.  
- **Cross-Device Application Migration**: Through cross-device migration and multi-device collaboration, users can enjoy a better experience. For example, a video playing on a tablet can be seamlessly transferred to a smart TV for continued playback.  

## Capability Scope  

- Provides capabilities for application process creation and destruction, as well as application lifecycle scheduling.  
- Offers capabilities such as application component runtime entry points, lifecycle scheduling for components, and inter-component interaction.  
- Delivers application context environments and system environment change monitoring.  
- Supports application migration capabilities.  
- Enables multi-package mechanisms, shared packages, and application information configuration. For details, refer to [Application Package Overview](../cj-start/basic-knowledge/application-package-overview.md).  
- Provides program access control capabilities. For details, refer to [Access Control Overview](../security/AccessToken/cj-access-token-overview.md).  

<!--RP1-->  
<!--RP1End-->  

## Highlights/Features  

1. **Designed for Complex Applications**  
   - Adopts an object-oriented development approach, ensuring high readability, maintainability, and extensibility for complex application code.  
   - Supports modular capability development.  

2. **Supports Cross-Device Migration and Multi-Device Collaboration at the Component Level**  
   The Stage model decouples application components from the UI.  
   - In cross-device migration scenarios, after the system transfers data/state between application components across devices, the UI can leverage ArkUI's declarative features to restore the user interface using the preserved data/state, enabling seamless cross-device migration.  
   - In multi-device collaboration scenarios, application components inherently support RPC-based inter-component communication, facilitating interaction between cross-device application components.  

3. **Supports Multi-Device and Multi-Window Forms**  
   Application component management and window management are architecturally decoupled.  
   - Facilitates system-level tailoring of application components (e.g., windowless devices can omit window-related components).  
   - Enables system-level extension of window forms.  
   - Application components can use the same lifecycle across multiple devices (e.g., desktop and mobile devices).  

4. **Balances Application Capabilities and System Management Costs**  
   The Stage model redefines the boundaries of application capabilities, balancing functionality and system control costs.  
   - Provides application components for specific scenarios (e.g., service cards, input methods) to accommodate diverse use cases.  
   - Standardizes background process management: To ensure a smooth user experience, the Stage model enforces orderly governance of background application processes. Applications cannot arbitrarily reside in the background, and their background behavior is strictly regulated to prevent malicious activities.  

## Relationship with Related Kits  

**ArkUI**: Within the UIAbility components of Ability Kit, developers can utilize ArkUI's capabilities, including components, events, animations, and state management.