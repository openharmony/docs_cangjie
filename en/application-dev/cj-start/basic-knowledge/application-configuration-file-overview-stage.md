# Overview of Application Configuration Files (Stage Model)

Each application project's code directory must contain application configuration files, which provide basic information about the application to compilation tools, the operating system, and application markets.

In application projects developed based on the Stage model, there exists an app.json5 configuration file and one or more module.json5 configuration files.

The [app.json5 configuration file](app-configuration-file.md#app.json5配置文件) contains the following:

- Global configuration information of the application, including basic details such as the application's Bundle name, developer/vendor, version number, etc.

- Configuration information for specific device types.

The [module.json5 configuration file](module-configuration-file.md#app.json5配置文件) contains the following:

- Basic configuration information of the Module, including fundamental details such as Module name, type, description, supported device types, etc.

- Permission information required during the application's runtime.