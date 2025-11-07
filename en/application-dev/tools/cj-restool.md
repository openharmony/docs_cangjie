# restool Tool  

## Introduction  

restool is an application engineering resource compilation tool that creates resource indexes and parses resources by compiling resource files. Developers can access corresponding resources by calling the [Resource Management Interface](../reference/LocalizationKit/cj-apis-resource_manager.md). The restool tool is located in the `toolchains` subdirectory of the SDK installation directory.  

## Parameter Description  

The restool currently supports the following command options:  

| Option | Optional | With Parameter | Description |  
|--------|----------|----------------|-------------|  
| -i | Required | With parameter | Specifies the resource directory to be compiled or the resource middleware to be built. This command can be specified multiple times in the same command. <br>For details, refer to [Compile Resource Command](#compile-resources). |  
| -j | Required | With parameter | Specifies the path of the `config.json` or `module.json` file. |  
| -o | Required | With parameter | Specifies the output path for compiled resources. |  
| -p | Required | With parameter | Specifies the bundle name of the compiled resources. |  
| -r | Required | With parameter | Specifies the header file path for resources, with three formats: `.txt`, `.js`, or `.h`. |  
| -e | Optional | With parameter | Specifies the starting ID value for generated resources, e.g., `0x01000000`. Valid ranges: `[0x01000000, 0x06FFFFFF)`, `[0x08000000, 0x41FFFFFF)`. |  
| -f | Optional | Without parameter | If the output path already exists, forcibly delete and regenerate it. |  
| -h | Optional | Without parameter | Displays tool help information. |  
| -m | Optional | With parameter | Specifies multiple module names for multi-module joint compilation, connected by commas. |  
| -x | Optional | With parameter | Specifies the resource directory or single resource path for generating intermediate files. This command can be specified multiple times in the same command. |  
| -z | Optional | Without parameter | Generates compilation results for the resource intermediate file directory. |  
| -v | Optional | Without parameter | Displays the tool version number. |  
| --ids | Optional | With parameter | Specifies the output directory for generating `id_defined.json`. |  
| --defined-ids | Optional | With parameter | Specifies the path of the `id_defined.json` file, typically generated via `--ids`. <br>`id_defined.json` contains a list of resource types, names, and their IDs. <br>Developers can customize resource IDs in `id_defined.json`. |  
| --icon-check | Optional | Without parameter | Enables PNG image validation for `icon` and `startWindowIcon`. |  
| --target-config | Optional | With parameter | Used with the `-i` command to support selective compilation. <br>[Parameter Description](#target-config-parameter-description): Specifies the configurations to include. |  

### target-config Parameter Description  

Supported parameter configuration types: `MccMnc`, `Locale`, `Orientation`, `Device`, `ColorMode`, `Density`.  

Parameter format: Configurations are separated by `;`, and values within configurations are enclosed in `[]` and separated by `,`.  

**MccMnc Matching Rules**:  
- Mcc (country code) must be the same.  
- Mnc (network code) defaults to a match if absent; otherwise, Mnc must be the same.  

**Locale Matching Rules**:  
Locale matching must satisfy the following three rules:  
1. Language must be the same.  
2. Script (writing system) defaults to a match if absent; otherwise, it must be the same.  
3. Country or region defaults to a match if absent; otherwise, it must be the same.  

**Example Parameter**:  
`Locale[zh_CN,en_US];Device[phone]`  
- This parameter filters out other languages, retaining only those matching `zh_CN` and `en_US`.  
- Filters out other devices, retaining only `phone`.  
- Other configurations (e.g., `MccMnc`, `Orientation`) are not filtered and are retained.  

## Usage Examples  

For example, the directory structure of `entry` is as follows:  

```text  
entry/src/main  
|    |----resource  
|    |    |----base  
|    |    |    |----element  
|    |    |    |----media  
|    |    |    |----profile  
|    |    |----rawfile  
|    |    |----resfile  
|    |----config.json/module.json  
```  

### Compile Resources  

There are two ways to compile resources: full resource compilation and incremental resource compilation.  

1. **Full Resource Compilation**:  
   Command:  

    ```bash  
    restool -i entry/src/main -j entry/src/main/module.json -p com.ohos.demo -o out -r out/ResourceTable.txt -f  
    ```  

2. **Incremental Resource Compilation**:  
   Steps:  

   **Step 1**: Generate resource middleware. Command:  

    ```bash  
    restool -x entry/src/main/resource -o out  
    ```  

   **Step 2**: Compile resource middleware. Command:  

    ```bash  
    restool -i out1 -i out2 -o out -p com.ohos.demo -r out/ResourceTable.txt -j entry/src/main/module.json -f -z  
    ```  

### Fix Resource IDs  

To fix resource IDs, follow these steps:  

**Step 1**: Create the `id_defined.json` file. There are two methods: via command line or custom creation.  

- **Method 1**: Generate via command line. Command:  

    ```bash  
    restool -i entry/src/main -j entry/src/main/module.json -p com.ohos.demo -o out -r out/ResourceTable.txt --ids out -f  
    ```  

- **Method 2**: Custom file. The filename must be `id_defined.json`, with the following content:  

    ```json  
    {  
        "record" :  
        [  
            {  
                "id" : "0x01000000", // The fixed ID value for the resource  
                "name" : "app_name", // Resource name  
                "type" : "string"    // Resource type  
            }  
        ]  
    }  
    ```  

**Step 2**: Fix the resource IDs. There are two ways:  

- **Command 1**:  

    ```bash  
    restool -i entry/src/main -j entry/src/main/module.json -p com.ohos.demo -o out1 -r out1/ResourceTable.txt --defined-ids out/id_defined.json -f  
    ```  

- **Command 2**: Place the custom `id_defined.json` in the `resource/base/element/` directory, then run:  

    ```bash  
    restool -i entry/src/main -j entry/src/main/module.json -p com.ohos.demo -o out1 -r out1/ResourceTable.txt -f  
    ```