# Introduction to Test Kit  

Test Kit provides developers with an automated testing framework that offers unit testing and UI testing capabilities. It supports writing unit and UI automated test scripts in the Cangjie language, allowing developers to verify the implementation effects of corresponding features through test results.  

**Unit Testing Capabilities:**  

Provides fundamental interfaces and execution mechanisms for automated testing, with the following key features:  

- Offers interfaces for defining automated test cases, including test suite definition and test case definition.  
- Provides assertion interfaces for automated test cases, supporting multiple assertion methods and enabling flexible usage in automated scripts.  
- Includes interfaces for executing setup/teardown actions, supporting execution at both the test suite and test case levels.  
- Supports multiple test execution modes, such as selective execution of specified test cases, random execution, and stress testing.  

**UI Testing Capabilities:**  

Provides UI automated testing capabilities, with script execution built upon the unit testing framework. Key features include:  

- Offers control lookup interfaces, supporting various methods such as searching by control attributes or relative positions.  
- Provides simulated UI operation interfaces, supporting actions like clicks, double-clicks, swipes, and pinch-to-zoom, as well as simulating input from peripherals such as mice and keyboards.  
- Includes simulated window operation interfaces, supporting actions like resizing and moving windows.  
- Enables shell command-based simulation of UI operations, such as clicks, double-clicks, and swipes.  
- Supports monitoring system dialogs/toasts and retrieving prompt text.  

For detailed usage instructions, please refer to the [Automated Testing Framework User Guide](./cj-arkxtest-guidelines.md).