# Application File Overview  

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

Application Files: Files owned by the application, including installation files, resource files, cache files, etc.  

- Data used and stored by applications on the device is saved in an application-specific directory in the form of files, key-value pairs, databases, etc. This dedicated directory is called the "Application File Directory," where all data is stored in various file formats. These files are referred to as application files.  

- The "Application File Directory" and a subset of system files (essential system files required for application operation) form a collective entity known as the "[Application Sandbox Directory](./cj-app-sandbox-directory.md#应用沙箱目录)." This represents the entire scope of directories visible to the application. Therefore, the "Application File Directory" resides within the "Application Sandbox Directory."  

- System files and their directories are read-only for applications. Applications can only save files under the "[Application File Directory](./cj-app-sandbox-directory.md#应用文件目录与应用文件路径)." Based on directory usage guidelines and considerations, data should be saved to different subdirectories accordingly.  

The following sections will detail application sandboxing, the application file directory, application file access and management, application file sharing, and related topics.